# PowerShell Script to Fetch the Lockout Sources of the User in Active Directory
```
$UserName = Read-Host "Please enter username:"
$PDC = (Get-ADDomainController -Filter * | Where-Object {$_.OperationMasterRoles -contains "PDCEmulator"})
$UserInfo = Get-ADUser -Identity $UserName
$LockedOutEvents = Get-WinEvent -ComputerName $PDC.HostName -FilterHashtable @{LogName='Security'; Id=4740} -ErrorAction Stop | Sort-Object -Property TimeCreated -Descending

Foreach ($Event in $LockedOutEvents) {
    If ($Event.Properties[2].Value -match $UserInfo.SID.Value) {
        $Event | Select-Object -Property @(
            @{Label = 'User'; Expression = {$_.Properties[0].Value}},
            @{Label = 'DomainController'; Expression = {$_.MachineName}},
            @{Label = 'EventId'; Expression = {$_.Id}},
            @{Label = 'LockoutTimeStamp'; Expression = {$_.TimeCreated}},
            @{Label = 'Message'; Expression = {$_.Message -split "`r" | Select-Object -First 1}},
            @{Label = 'LockoutSource'; Expression = {$_.Properties[1].Value}}
        )
    }
}

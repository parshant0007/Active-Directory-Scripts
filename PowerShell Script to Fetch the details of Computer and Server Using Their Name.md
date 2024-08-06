# PowerShell Script to Fetch the details of Computer and Server Using Their Name

---
$domains = "Domain1", "Domain2","Domain3","Domain4" 
$users = Get-content 'C:\Users\sharma.pr.adm\Desktop\ScriptOU\mohitup.csv'                                           
foreach($Domain in $Domains)                                                 
{
foreach ($User in $users)
{
Get-ADComputer $User -Server $domain -Properties * | Select CN, dNSHostName, distinguishedName, operatingSystem, enabled, lastLogonTimestamp, pwdLastSet, whenChanged, whenCreated | Export-Csv 'C:\Users\sharma.pr.adm\Desktop\ScriptOU\mohit.csv' -NoTypeInformation -APPEND -ErrorAction SilentlyContinue
}
} 
--

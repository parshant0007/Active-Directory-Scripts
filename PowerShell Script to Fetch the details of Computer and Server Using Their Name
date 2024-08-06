# PowerShell Script to Fetch the details of Computer and Server Using Their Name

---
$domains = "emea.corp.geaag.com", "ap.corp.geaag.com","am.corp.geaag.com","corp.geaag.com" 
$users = Get-content 'C:\Users\sharma.pr.adm\Desktop\ScriptOU\mohitup.csv'                                           
foreach($Domain in $Domains)                                                 
{
foreach ($User in $users)
{
Get-ADComputer $User -Server $domain -Properties * | Select CN, dNSHostName, distinguishedName, operatingSystem, enabled, lastLogonTimestamp, pwdLastSet, whenChanged, whenCreated | Export-Csv 'C:\Users\sharma.pr.adm\Desktop\ScriptOU\mohit.csv' -NoTypeInformation -APPEND -ErrorAction SilentlyContinue
}
} 
--

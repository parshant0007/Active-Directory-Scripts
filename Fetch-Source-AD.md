```
Get-ADComputer -Filter * -Properties * | Select CN, dNSHostName, distinguishedName, operatingSystem, enabled, lastLogonTimestamp, pwdLastSet, whenChanged, whenCreated | Export-Csv 'C:\Users\sharma.pr.adm\Desktop\Prash\netscaler\rinit.csv' -NoTypeInformation -APPEND -ErrorAction SilentlyContinue
 

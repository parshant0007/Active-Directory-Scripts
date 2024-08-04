# Script To Retrieve or Fetch Computer and Server Information From The Entire Active Directory Including Attributes (Such as Machine Name, OU, OS Name, Enabled, Last Logon Time, etc.)
---
Get-ADComputer -Filter * -Properties * | Select CN, dNSHostName, distinguishedName, operatingSystem, enabled, lastLogonTimestamp, pwdLastSet, whenChanged, whenCreated | Export-Csv 'Enter Export Path' -NoTypeInformation -APPEND -ErrorAction SilentlyContinue
 
---

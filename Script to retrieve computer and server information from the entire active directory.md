#Script to retrieve computer and server information from the entire active directory including attributes (such as machine name, OU, OS name, enabled, last logon time, etc.)

Get-ADComputer -Filter * -Properties * | Select CN, dNSHostName, distinguishedName, operatingSystem, enabled, lastLogonTimestamp, pwdLastSet, whenChanged, whenCreated | Export-Csv 'Enter Export Path' -NoTypeInformation -APPEND -ErrorAction SilentlyContinue
 

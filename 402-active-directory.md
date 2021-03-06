# Active Directory

## Task 1: Active Directory basics
1. Open a new Powershell session.
1. Run this command: ```Get-Command *user*```
1. Notice the ActiveDirectory module in the Source column.
1. Get a listing of all commands from the ActiveDirectory module: ```Get-Command -Module ActiveDirectory```
1. Measure the total number of commands from the ActiveDirectory module: ```Get-Command -Module ActiveDirectory | Measure-Object```
1. Run this command to get all the computers from AD: ```Get-ADComputer -filter *```


## Task 2: Active Directory user management
1. Run this command to create a new useraccount in AD:
1. ```New-ADUser -Name 'Jane Doe' -Department 'IT'```
1. Inspect the new account: ```Get-ADUser -Name 'Jane Doe'```
1. The Enabled property is false.
1. Try to enable the account with this command: ```Enable-ADAccount -Identity 'Jane Doe'```
1. An error message is displayed because the password is not set or not complex enough.
1. Create a password, and convert it to a secure string:
1. ```$pw = Convertto-SecureString -String 'Pa55w.rd' -AsPlainText -Force```
1. Set the password: ```Set-ADAccountPassword -Identity 'Jane Doe' -NewPassword $pw -Reset```
1. Enable the account: ```Enable-ADAccount -Identity 'Jane Doe'```
1. Notice the account has been enabled.
1. To create a new user, with a password and enabled it, run this command:
1. ```New-ADUser -Name 'John Doe' -Department 'IT' -Enabled $true -AccountPassword (Convertto-SecureString -String 'Pa55w.rd' -AsPlainText -Force)```
1. Inspect both users with this command: ```Get-ADUser -filter * | Where-Object Name -match 'Doe'```
1. Run this command to set properties on a user object:
1. ```Set-ADuser Lara -StreetAddress 'Sunset blvd.' -City 'Los Angeles' -State 'CA' -Country 'USA'```
1. Run this command to retrieve an user object:
1. ```Get-ADuser Lara```
1. Notice it contains few properties.
1. Run this command to inspect an user object:
1. ```Get-ADuser Lara | Get-Member```
1. Notice it still contains few properties. This is because most properties are only retrieved on request.
1. Run this command to retrieve specific properties of an user object:
1. ```Get-ADuser Lara -Properties StreetAddress,City,State,Country```
1. Notice the desired properties are displayed.


## Task 3: Active Directory group management
1. Run this command to list all group commands in the Active Directory module:
1. ```Get-Command -Module ActiveDirectory -Noun *Group*```
1. Run this command to create a Helpdesk Group in AD:
1. ```New-ADGroup -Name Helpdesk -Path 'ou=IT,dc=Adatum,dc=com' –GroupScope Global```
1. Run this command to add two users to the Helpdesk group:
1. ```Add-ADGroupMember -Identity 'HelpDesk' -Members 'Lara','Jane Doe'```
1. Run this command to inspect the properties of the Helpdesk group:
1. ```Get-ADGroup -Identity 'HelpDesk'```
1. Run this command to inspect the Helpdesk group members:
1. ```Get-ADGroupMember -Identity 'HelpDesk'```


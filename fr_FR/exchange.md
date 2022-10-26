# Exchange

## Lancer les services Exchanges
```sh
Get-service -name "msexchange*" -dependentservices | Where-Object {$_.Status -eq 'stopped'} | Start-Service
```
## Permissions des boites emails
 -  [Get-MailboxFolderPermission](https://learn.microsoft.com/en-us/powershell/module/exchange/get-mailboxfolderpermission?view=exchange-ps)  
 - [Set-MailboxFolderPermission](https://learn.microsoft.com/en-us/powershell/module/exchange/set-mailboxfolderpermission?view=exchange-ps)  
Exemple:  
```sh
Set-MailboxFolderPermission -Identity "example@contoso.com:\Calendrier" -User "Default" -AccessRights "LimitedDetails"
```
```sh
Get-MailboxFolderPermission -Identity "example@contoso.com:\Calendrier"

FolderName           User                 AccessRights
----------           ----                 ------------
Calendrier           Par défaut           {LimitedDetails}
Calendrier           Anonyme              {None}
```

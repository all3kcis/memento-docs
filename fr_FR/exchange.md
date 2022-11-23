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

## Santé des services  
`Get-ExchangeServer | Test-ServiceHealth`

## Reconfiguration des services nécessaires  
```sh
# Exchange 2019 list
# https://learn.microsoft.com/fr-fr/exchange/plan-and-deploy/deployment-ref/services-overview?view=exchserver-2019

Set-Service -Name "MSExchangeADTopology" -StartupType Automatic
Set-Service -Name "MSExchangeAntispamUpdate" -StartupType Automatic
Set-Service -Name "MSComplianceAudit" -StartupType Automatic
Set-Service -Name "MSExchangeCompliance" -StartupType Automatic
Set-Service -Name "MSExchangeDagMgmt" -StartupType Automatic
Set-Service -Name "MSExchangeDiagnostics" -StartupType Automatic
Set-Service -Name "MSExchangeEdgeSync" -StartupType Automatic
Set-Service -Name "MSExchangeMitigation" -StartupType Automatic
Set-Service -Name "MSExchangeFrontEndTransport" -StartupType Automatic
Set-Service -Name "MSExchangeHM" -StartupType Automatic
Set-Service -Name "MSExchangeHMRecovery" -StartupType Automatic
Set-Service -Name "Msexchangeis" -StartupType Automatic
Set-Service -Name "MSExchangeMailboxAssistants" -StartupType Automatic
Set-Service -Name "MSExchangeMailboxReplication" -StartupType Automatic
Set-Service -Name "MSExchangeDelivery" -StartupType Automatic
Set-Service -Name "MSExchangeSubmission" -StartupType Automatic
Set-Service -Name "MSExchangeRepl" -StartupType Automatic
Set-Service -Name "MSExchangeRPC" -StartupType Automatic
Set-Service -Name "MSExchangeFastSearch" -StartupType Automatic
Set-Service -Name "HostControllerService" -StartupType Automatic
Set-Service -Name "MSExchangeServiceHost" -StartupType Automatic
Set-Service -Name "MSExchangeThrottling" -StartupType Automatic
Set-Service -Name "Msexchangetransport" -StartupType Automatic
Set-Service -Name "MSExchangeTransportLogSearch" -StartupType Automatic

# Servers Transport Edge
Set-Service -Name "MSExchangeAntispamUpdate" -StartupType Automatic
Set-Service -Name "MSExchangeDiagnostics" -StartupType Automatic
Set-Service -Name "MSExchangeHM" -StartupType Automatic
Set-Service -Name "MSExchangeHMRecovery" -StartupType Automatic
Set-Service -Name "MSExchangeServiceHost" -StartupType Automatic
Set-Service -Name "Msexchangetransport" -StartupType Automatic
Set-Service -Name "MSExchangeTransportLogSearch" -StartupType Automatic
```

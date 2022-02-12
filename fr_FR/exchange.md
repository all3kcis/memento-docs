# Exchange

## Lancer les services Exchanges
```sh
Get-service -name "msexchange*" -dependentservices | Where-Object {$_.Status -eq 'stopped'} | Start-Service
```

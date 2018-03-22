# ESXI
## Voir l'etat SMART d'un disque
```sh
/./usr/lib/vmware/vm-support/bin/smartinfo.sh
```
## Issues
- [AHCI performance issue](https://www.virtuallyghetto.com/2017/07/ahci-vmw_ahci-performance-issue-resolved-in-esxi-6-5-update-1.html)  
```sh
esxcli system module list | grep vmw_ahci
esxcli system module set --enabled=true --module=vmw_ahci
```

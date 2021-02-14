# ESXI
## Voir l'etat SMART d'un disque
```sh
/./usr/lib/vmware/vm-support/bin/smartinfo.sh
```

## Activer Multipath sur ISCSI
`esxcli storage core path list`  
`esxcli storage nmp device list` verifier la ligne : Working Paths  
Voir quel mode est actif `esxcli storage nmp device list -d "naa.6589cfc000000e0360243f01854e371f" | grep PSP` ex : `Path Selection Policy: VMW_PSP_MRU`  
Définir sur RoundRobin `esxcli storage nmp device set -d "naa.6589cfc000000e0360243f01854e371f" --psp=VMW_PSP_RR`  
Result `esxcli storage nmp device list -d "naa.6589cfc000000e0360243f01854e371f" | grep PSP`:  `Path Selection Policy: VMW_PSP_RR`   
Puis vérifier les chemins avec `esxcli storage nmp device list`

Voir les chemin pour : `esxcli storage core path list -d "naa.6589cfc000000e0360243f01854e371f"`  
Liste carte réseau `esxcfg-nics -l`

## Issues
- [AHCI performance issue](https://www.virtuallyghetto.com/2017/07/ahci-vmw_ahci-performance-issue-resolved-in-esxi-6-5-update-1.html)  
```sh
esxcli system module list | grep vmw_ahci
esxcli system module set --enabled=true --module=vmw_ahci
```

### Si le port ne remonte pas automatique
Tester `esxcli network nic up -n vmnic0` si ça ne fonctionne pas, faire : `esxcli network nic set -n vmnic0 -a`

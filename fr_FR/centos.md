# CentOs
  
## Configurer une interface réseau sous CentOs  
### Créer un fichier interface  
`cd /etc/sysconfig/network-scripts`  
Remplacer eth0 par la valeur voulu, eth1 par exemple pour une seconde carte réseau
`nano ifcfg-eth0`  
Infos de base :  
```sh
# Nom du périphérique
DEVICE=eth0
# Activation au démarrage
ONBOOT=yes
# Nom de l’interface
NAME=lan
# Adresse MAC de l’interface
MAC=<MAC ADRESS>
```  
Paramètres supplémentaires :  
```sh
BOOTPROTO=dhcp # Dans le cas de l'utilisation avec un DHCP
GATEWAY=192.168.1.254
```  
**A savoir, l'option GATEWAY, permet de se prémunir des attaques DHCP snooping**  
#### IP fixe  
```sh
# IP de l’interface
IPADDR=192.168.1.1
# Masque de sous réseau
NETMASK=255.255.255.0
# IP du réseau
NETWORK=192.168.1.0
# IP de Broadcast
BROADCAST=192.168.1.255
# IP de la passerelle
GATEWAY=192.168.1.254
```  
#### Activation de l'interface  
`ifup eth0`  
#### Redemarrage de l'interface réseau
`service network restart`  

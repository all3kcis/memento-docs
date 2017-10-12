# Exim4

## Commandes utiles
> Source : http://howto.landure.fr/gnu-linux/trucs-et-astuces-pour-exim-4  
> https://buzut.fr/connaitre-commandes-dompter-exim4/

**Voir les messages de la file d'attente**  
```
mailq
```  
**Supprimer un message de la file d'attente** 

```
exim -Mrm <id_msg>
```  
**Supprimer tous les messages de la file d'attente**  
```
exim4 -Mrm `ls /var/spool/exim4/input/ | grep -- -H$ | cut -c 1-16`
```
**Retenter la livraison de tous les messages présents dans la file d'attente**
```
exim4 -qff
```
**Obtenir la liste des messages gelés**
```
mailq | grep "frozen"
```
**Retenter la livraison d'un message**
```
exim4 -M <id_msg>
```
**Retenter la livraison de tous les messages "gelés" de la file d'attente**
```
mailq | grep frozen | sed -e 's/.* \(.\{6\}-.\{6\}-.\{2\}\) .*/\1/' | xargs exim4 -M
```
**Supprimer tous les messages "gelés" de la file d'attente**
```
mailq | grep frozen | sed -e 's/.* \(.\{6\}-.\{6\}-.\{2\}\) .*/\1/' | xargs exim4 -Mrm
```
**Afficher le contenu d'un message de la file d'attente**
```
exim4 -Mvb <id_msg>
```
**Obtenir des statistiques sur l'activité d'Exim**
```
eximstats /var/log/exim4/mainlog
```
**Nettoyer le spool**
```
exim_tidydb -t 7d /var/spool/exim4/ retry
exim_tidydb -t 7d /var/spool/exim4/ misc
exim_tidydb -t 7d /var/spool/exim4/ wait-amavis
exim_tidydb -t 7d /var/spool/exim4/ wait-remote_smtp
```

## Parametrage smarthost relay
Commande pour configuration en graphique : `dpkg-reconfigure exim4-config`  
Le fichier `/etc/exim4/update-exim4.conf.conf`  
Devrait ressembler à  

```
dc_eximconfig_configtype='smarthost'
dc_other_hostnames=''
dc_local_interfaces='127.0.0.1 ;'
dc_readhost='<readhost>'
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost='<smtp_address>::465'
CFILEMODE='644'
dc_use_split_config='true' 		# Important
dc_hide_mailname='true'
dc_mailname_in_oh='true'
dc_localdelivery='mail_spool'
```

**Puis editer** `/etc/exim4/conf.d/transport/30_exim4-config_remote_smtp_smarthost `  
Ajouter les lignes suivante dans le bloc `remote_smtp_smarthost:`
```
protocol = smtps
hosts_require_auth = <smtp_address>
```

**Et enfin fichier** `/etc/exim4/passwd.client`  
```
<smtp_address>:<login_or_email>:<passwd>
```

## Redirection mails de root
Modifier le fichier `/etc/exim4/conf.d/rewrite/00_exim4-config_header`  
Ajouter la ligne `root@* new_user@domaine.com`

## Mettre à jour la configuration
`update-exim4.conf`  
puis `service exim4 restart`  

## Sources  
http://bradthemad.org/tech/notes/exim_cheatsheet.php  
https://www.jbnet.fr/systeme/linux/debian-rediriger-les-emails-root-et-autres-utilisateurs-avec-exim4.html  

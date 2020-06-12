# TODO

## Git
 * bisect
Retourner a un ancien commit  
git checkout 6df1g1 (id du commit)  

Retourner au dernier commit (plus recent)  
git checkout master  


## GNU
> https://www.debian.org/doc/manuals/debian-reference/ch09.fr.html
 * ~/.bashrc
 * alias ls='ls --time-style=+%d.%m.%y\ %H:%M'
 * alias l='ls $LS_OPTIONS -lAh --group-directories-first --time-style=+%d.%m.%y\ %H:%M'
 * 9.3.7 : fuser -v /var/log/mail.log
 * 9.3.8 : watch w
 * 9.3.13 : at / cron
 * 9.4.1 : who
 * 9.4.2 : wall
 * 9.4.5 : definir heure
 * chattr +i
 * scp <file> <username>@<IP address or hostname>:<Destination>
 
 * du -h --max-depth=1 /  
 * df -h  
 http://unix.stackexchange.com/questions/87908/how-do-you-empty-the-buffers-and-cache-on-a-linux-system  
 
 apt-mark hold apache2  
 apt-mark unhold apache2  
 
 `find . ! -perm -o=r` trouver fichier sans perm de lecture
   
 **Mount CIFS**
   https://blog.tomecek.net/post/automount-with-systemd/
 
 ### Generer mdp aleatoire  
 tr -cd '[:alnum:]' < /dev/urandom | fold -w12 | head -n1
 
## PHP
 * Xdebug max value : https://xdebug.org/docs/all_settings#var_display_max_children

## Duplicity
 duplicity collection-status file:///path-backups/  
 duplicity --file-to-restore path/to/restore  file:///path/backups /path/to/restore  
 -option  --no-encryption

## OpenSSL
Revoquer certificat  
openssl ca -revoke newcerts/01.pem -config openssl.cnf  

## SQl

### Construire une requete de suppression de tables en fonction du préfix  
```sql
SELECT CONCAT( 'DROP TABLE ', GROUP_CONCAT(table_name) , ';' ) 
    AS statement FROM information_schema.tables 
    WHERE table_schema = 'database_name' AND table_name LIKE 'prefix_%';
```


## Docker
```
docker build -t <username>/<repo>:<tag>
docker run --name <doc_name> -p 8585:80 -dit <username>/<repo>:<tag>
docker run --name <doc_name> -p 8585:80 -v $(pwd):/var/www/html/ -dit <username>/<repo>:<tag>
docker exec -ti <name/hash> <cmd>
```

## ESXI Customizer
```
.\ESXi-Customizer-PS-v2.4.ps1 -izip .\VMware-VMvisor-Installer-6.0.0.update01-3029758.x86_64.zip -load .\VMware_bootbank_net-r8168_8.013.00-3vmw.510.0.0.799733.vib
.\ESXi-Customizer-PS-v2.4.ps1 -v60 -load -vft net-r8168
```
## EXIM4

http://howto.landure.fr/gnu-linux/trucs-et-astuces-pour-exim-4

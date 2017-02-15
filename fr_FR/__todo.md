# TODO

## Git
 * bisect

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

## FFMPEG
`ffmpeg -i in.mp4 -vcodec libx264 -f mp4 -preset veryslow -s 480x270 -acodec aac -ab 128k out.mp4`  
libx265 aussi possible


## SQl

### Construire une requete de suppression de tables en fonction du préfix  
```sql
SELECT CONCAT( 'DROP TABLE ', GROUP_CONCAT(table_name) , ';' ) 
    AS statement FROM information_schema.tables 
    WHERE table_schema = 'database_name' AND table_name LIKE 'prefix_%';
```

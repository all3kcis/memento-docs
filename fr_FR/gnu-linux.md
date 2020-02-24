# GNU/Linux
 - https://github.com/jlevy/the-art-of-command-line/blob/master/README-fr.md
 - https://github.com/dylanaraps/pure-bash-bible  
 - http://www.lestutosdenico.com/tutos-de-nico/netcat
 - https://www.guillaume-leduc.fr/outils-du-sysadmin-linux-ss.html
 - https://www.pcsuggest.com/linux-bluetooth-setup-hcitool-bluez/
 - https://www.christophe-casalegno.com/linux-fonctions-bash-que-jutilise-dans-mes-scripts-shell/

## Fichiers

### Modifications des droits
@Todo
*stickybit

### Copie sécurisé
`scp -P 2113 file user@hote:path`

### Télécharger des fichiers
`wget [url]`
`curl -O [url]`

### Compresser
`tar czvf [nom_archive].tar.gz [nom_rep]`

### Decompresser
`tar xzvf`

### Recherches
	- [Gnu.org - Find (EN)](https://www.gnu.org/software/findutils/manual/html_mono/find.html)  
	- [Debsousdeb - Find (FR)](http://debsousdeb.canalblog.com/archives/2006/01/08/1198709.html)

*Voir aussi* 
	- [All3kcis - Script recherche de fichier par extension](https://gist.github.com/all3kcis/1f5d736ee2a967a4523bbb24404367bc)
#### Rechercher une expression dans une liste de fichiers
```sh
  find . -type f -name "*.php" | xargs grep "base64_decode" --color
```
*Arguments*
>  - . = répertoire courant
>  - -type f = fichiers
>  - -name "" = pattern de recherche du nom des fichiers
>  - grep "" = expression à rechercher
>  - --color = pour mettre en evidence l'expression trouvée dans les résultats

#### Rechercher les derniers fichiers modifiés
```sh
  find . -type f -name "*.php" -mtime -7
```
*Arguments*
> - . = répertoire courant
> - -type f = fichiers
> - -name "" = pattern de recherche du nom des fichiers
> - -mtime -7 = dans les sept derniers jours
#### Suivre les modifications d'un repertoire en live  
`watch -n0,1 "ls -lrt /tmpdir/ | tail"`


## Packages

### Liste des packages installés
`dpkg-query -l`  

### Date d'installation
`zgrep -h " installed " /var/log/dpkg.log* | sort` ajouter si besoin : `| grep <nomdupackage>`  
**OU** Distri basée sur Red Hat  
`rpm -qa --last`

## Réseau
> https://www.binarytides.com/linux-commands-monitor-network/

### Test envoi mail  

`echo "Mail envoyé le $(date)" | mail -s "Test envoi de mail depuis $HOST" votre_adresse@exemple.com`

### Relancer l'interface réseau
`/etc/init.d/networking restart`

### Traceroute
`traceroute`
  
### Test fragmentation
`ping -M do -s X IP` pour tester si un paquet de taille X+28 (IPv4) ou X+48 (IPv6) arrive à IP sans fragmentation  

### Qui ecoute quoi
`netstat -nlp` `-latupe`

### Scan des host d'un réseau
`nmap -sP 192.168.1.0/24`  

### Tester un port
`nmap -p 80 192.168.1.10`  

### Ecouter un port avec netcat
> https://doc.fedora-fr.org/wiki/Netcat,_connexion_client/serveur_en_bash  
`nc -l 80`  

## SSH
 
**Recuperer les clés publiques d'un serveur**  
`ssh-keyscan -p <port> <host> > <your_file>`

**Obtenir les fingerpritn des clés**  
`ssh-keygen -lf <your_file>`

### WIFI
**Diagnostique**  
`watch -n 1 cat /proc/net/wireless`  
`iwconfig`

## Gestion

### Redirection Entrée/Sortie standard
> Astuce : redirection vers rien `>/dev/null`  

**Redirection sortie standard**  
`2>`  : redirige les erreurs dans un fichier (s'il existe déjà, il sera écrasé)  
`2>>` : redirige les erreurs à la fin d'un fichier (s'il n'existe pas, il sera créé)  
`2>&1`: redirige les erreurs au même endroit et de la même façon que la sortie standard.  

**Envoyer le résultat d'une commande dans un fichier**  
`>`, Ex: `ls > list.txt`  
Ou pour ne pas écraser le contenu du fichier déjà existant :  
`>>`, Ex: `ls >> list.txt`  

**Connecter sortie standard sur entrée standard**  
`|`, Ex : `ls -l | less`

**lancer une commande si la précédente a réussi**  
`ls foo && echo "J'ai un fichier foo."`

**lancer une commande si la précédente a échoué**  
`ls foo || echo "Je n'ai pas de fichier foo."`

### Affichage logs
Affichage des dernières lignes d'un fichier
```sh
tail -f fichier.log
```
Option `-n <chiffre>` pour définir le nombre de lignes
Option `-f` mode follow, suivre en français.

### Gestions des jobs
> **Astuce** : A utiliser avec la redirection de sortie standard.

**Lancer en tache de fond**  
Terminer la commande avec le signe `&` Ex: `sleep 60 &`  
La commande renverra quelque chose du style `[1] 4355` ou "1" est l'id du job et "4355" l'id du processus 

**Voir les jobs en cours**
> Pour l'utilisateur courant.  

Commande : `jobs`

**Passer un job au premier plan**  
`fg %1` où "1" représente l'id du job.

**Passer un job en arrière plan**  
Appuyer sur `CTRL+Z` pour mettre en pause le processus  
puis `bg %1` où "1" représente l'id du job.

**Tuer un job**  
`kill %1` où "1" représente l'id du job.

**Déposseder un job**  
Permet de garder le processus en arrière plan en quittant le shell.  
`disown -h %1` où "1" représente l'id du job.

**Lancer un job en dehors du terminal courant**  
Ex : `nohup sleep 50 &` la commande crée un fichier de log nommé nohup.out, permettant de consulter les messages qui auraient dû s'afficher sur la console.  
On pourra visionner le contenu comme ceci : `more nohup.out`

### Ajouter un utilisateur dans un groupe
`adduser user groupe`  
groupes secondaire `usermod -G groupe user`

### Retirer un utilisateur d'un groupe
`gpasswd -d user groupe`  

### Fichiers hosts
```
etc/hosts
etc/hostname
```

### Fichier sources.list
`/etc/apt/sources.list`

### Mémoire
#### Ajout SWAP
  - [Wiki Debian - Swap](https://wiki.debian.org/fr/Swap)

@Todo
```sh
swapon -s
free -m
```

### Utilisation Mémoire
Trie utilisation mémoire par process  
```sh
ps -e -orss=,args= | sort -b -k1,1n | pr -TW$COLUMNS
```
Supprimer cache  
```sh
echo 3 > /proc/sys/vm/drop_caches
```

### NTP
See : https://www.cyberciti.biz/faq/linux-unix-bsd-is-ntp-client-working/


### Autres
Supprimer les codes couleurs  
```sh
sed 's/\x1b\[[0-9;]*m//g'        # Remove color sequences only
sed 's/\x1b\[[0-9;]*[a-zA-Z]//g' # Remove all escape sequences
sed 's/\x1b\[[0-9;]*[mGKH]//g'   # Remove color and move sequences
sed 's/\x1b\[[0-9;]*[mGKF]//g'   # Remove color and move sequences
```
> See : https://superuser.com/questions/380772/removing-ansi-color-codes-from-text-stream



# GNU/Linux

## Fichiers

### Modifications des droits
@Todo

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

## Réseau

### Relancer l'interface réseau
`/etc/init.d/networking restart`

### Traceroute
`traceroute`

## Gestion

### Affichage logs
Affichage des dernières lignes d'un fichier
```sh
tail -f fichier.log
```
Option `-n <chiffre>` pour définir le nombre de lignes
Option `-f` mode follow, suivre en français.

### Gestions des jobs

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

### Ajouter un utilisateur dans un groupe
`adduser user groupe`

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

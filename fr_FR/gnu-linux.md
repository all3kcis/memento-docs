#GNU/Linux

**Relancer l'interface réseau**
`/etc/init.d/networking restart`

**Affichage logs**

Affichage des dernières lignes d'un fichier
```sh
tail -f fichier.log
```
Option `-n <chiffre>` pour définir le nombre de lignes
Option `-f` mode follow, suivre en français.

**Copie sécurisé**
`scp -P 2113 file user@hote:path`

**Ajouter un utilisateur dans un groupe**
`adduser user groupe`

**Fichiers hosts**
```
etc/hosts
etc/hostname
```
**Télécharger des fichiers**
`wget [url]`
`curl -O [url]`

**Compresser**
`tar czvf [nom_archive].tar.gz [nom_rep]`

**Decompresser**
`tar xzvf`

**Fichier sources.list**
`/etc/apt/sources.list`

** Autres**
`traceroute`

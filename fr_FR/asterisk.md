# Asterisk
https://www.provya.net/?d=2015/06/24/08/18/10-asterisk-les-commandes-utiles-pour-asterisk
  
  **Suppression messages vocaux**  
 [Voir Gist - vmspool_manager.pl](https://gist.github.com/all3kcis/e10877ce02a17d10e35dac0bea76bede)  

  
**Afficher les redirections (callforward) actives**  
`asterisk -rx "database show CF"`

**Définir une redirections (callforward)**  
`asterisk -rx "database put CF <ext> <number>"`  

**Supprimer une redirection**  
> CF/CFU/CFB  
`asterisk -rx "database del CF <ext>"`  


**Supprimer toutes les redirections**  
`asterisk -x 'database show'|grep -r "^/CF"|cut -d ":" -f1|awk -F/ '{print "rasterisk -x \" database del " $2 " " $3 "\"" }' > sh.tmp;sh sh.tmp;rm sh.tmp`  

**Voir les communications en cours**  
`asterisk -rx "core show channels"`

**Détail d'une communication en cours**  
`asterisk -rx "core show channel <channel_name>"`

**Observer la perte de paquets sur une communication**  
`asterisk -rx "sip show channelstats"`

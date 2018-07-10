# Asterisk
https://www.provya.net/?d=2015/06/24/08/18/10-asterisk-les-commandes-utiles-pour-asterisk
  
**Afficher les redirections (callforward) actives**  
`asterisk -rx "database show CF"`

**Voir les communications en cours**  
`asterisk -rx "core show channels"`

**Détail d'une communication en cours**  
`asterisk -rx "core show channel <channel_name>"`

**Observer la perte de paquets sur une communication**  
`asterisk -rx "sip show channelstats"`

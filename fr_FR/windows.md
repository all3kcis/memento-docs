#Windows

**Réinitialiser le réseau**
> Commandes à exécuter en administrateur,
> puis relancer l'ordinateur
```sh
netsh int ip reset
netsh winsock reset catalog
```

**Fermer les connexions sur les lecteurs réseaux**
`net use * /delete`

**Autoriser un utilisateur à éteindre l'ordinateur à distance**
> Démarrer -> Exécuter -> "**gpedit.msc**"
à gauche, aller à :
Config. ordinateur / Paramètres Windows / Paramètres de sécurité / Stratégies locales / Attributions des droits utilisateurs
à droite, item "**Forcer l'arrêt à partir d'un distance**"
Vérifier (au besoin le rajouter) que l'utilisateur est autorisé

**Pour connecter un compte automatiquement**
Exécuter : `netplwiz`

**Autres**
`tracert`
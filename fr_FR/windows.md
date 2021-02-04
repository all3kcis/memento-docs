# Windows
## Réseau
### Réinitialiser le réseau
> Commandes à exécuter en administrateur,
> puis relancer l'ordinateur
```sh
netsh int ip reset
netsh winsock reset catalog
```
### Wifi
```sh
netsh wlan show profile
netsh wlan show profile SSID key=clear
```


**Fermer les connexions sur les lecteurs réseaux**  
`net use * /delete`  
OR  
WIN + R  
`rundll32.exe keymgr.dll, KRShowKeyMgr`

**Autoriser un utilisateur à éteindre l'ordinateur à distance**
> Démarrer -> Exécuter -> "**gpedit.msc**"
à gauche, aller à :
Config. ordinateur / Paramètres Windows / Paramètres de sécurité / Stratégies locales / Attributions des droits utilisateurs
à droite, item "**Forcer l'arrêt à partir d'un distance**"
Vérifier (au besoin le rajouter) que l'utilisateur est autorisé

**Pour connecter un compte automatiquement**
Exécuter : `netplwiz`

**Ajouter une route reseau**
```
> route ADD 157.0.0.0 MASK 255.0.0.0 157.55.80.1 METRIC 3 IF 2
         destination^      ^mask     ^gateway     metric^    ^
                                                    Interface^
```

**Autres**  
`tracert`

## Forcer la suppression d'un repertoire
`rd /s /q "\\?\D:\chemin_repertoire"`

## PowerShell  
**Executer des scripts non signés**  
Voir la configuratuin actuel  
`Get-ExecutionPolicy`  
Permettre l'utilisation de scripts non signés  
`Set-ExecutionPolicy unrestricted`

## Time

### Infos synchro temps (NTP)  
`w32tm /query /status`
> HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\NtpClient

## Tree
```sh
c:\>Tree /?
Graphically displays the folder structure of a drive or path.

TREE [drive:][path] [/F] [/A]

   /F   Display the names of the files in each folder.
   /A   Use ASCII instead of extended characters.
```
`tree > tree.txt /a /f`


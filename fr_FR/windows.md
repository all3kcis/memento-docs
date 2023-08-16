# Windows

*Bypass M$ account - New install*
`OOBE\BYPASSNRO`

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

### Modification timezone
`tzutil /g` Timezone actuel  
`tzutil /l` Lister Timezones  
`tzutil /s "Romance Standard Time"` Définir un timezone  

## Tree
```sh
c:\>Tree /?
Graphically displays the folder structure of a drive or path.

TREE [drive:][path] [/F] [/A]

   /F   Display the names of the files in each folder.
   /A   Use ASCII instead of extended characters.
```
`tree > tree.txt /a /f`  
`tree > "$((get-item $pwd).Name).txt" /A`

## WMIC
### Lister les utilisateurs et leurs SID
`wmic useraccount get name, sid`  
Pour un utilisateur en particulier  `wmic useraccount where name="username" get` ou `wmic useraccount where name='%username%' get sid`  
Utilisateur d'un domaine `whoami /user`  
Local administrateur `wmic useraccount where (name='administrator' and domain='%computername%') get name,sid`  
Domaine administrateur `wmic useraccount where (name='administrator' and domain='%userdomain%') get name,sid`  
Trouver utilisateur correspondant au SID `wmic useraccount where sid='S-1-3-12-1234....' get name`  

### Groups lsit of user
`net user /domain <username>`  

## Updates
### Remove download but not installed update
```
Go to C:\Windows\SoftwareDistribution\Download, and delete all contents. 
Open CMD, and type in net stop wuauserv.
Now type in net start wuauserv.
```


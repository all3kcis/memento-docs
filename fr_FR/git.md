# Git

**Force pull**
```sh
git reset --hard <repo>/<branch>
```

<a name="l2"></a>**Ignorer (temporairement) des fichiers déjà tracker**
```sh
# Pour ignorer
git update-index --assume-unchanged <file>

# Pour reconsidérer
git update-index --no-assume-unchanged <file>
```

**Voir les fichiers ignorer "assume-unchanged"**
```sh
git ls-files -v | grep '^[[:lower:]]'
```
Créer un alias
```
[alias]
	ignored = !git ls-files -v | grep "^[[:lower:]]"
```

**Exclure des fichiers sans .gitignore**
> Si les fichiers sont déjà suivi cela ne fonctionne pas.   
> Voir [Ignorer (temporairement) des fichiers déjà tracker](#l2)

Editer fichier : ` .git/info/exclude `
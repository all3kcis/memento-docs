# Git

## Commandes

**Force pull**
```sh
git reset --hard <repo>/<branch>
```

<a name="l2"></a>**Ignorer (temporairement) des fichiers déjà trackés**
```sh
# Pour ignorer
git update-index --assume-unchanged <file>

# Pour reconsidérer
git update-index --no-assume-unchanged <file>
```

**Voir les fichiers ignorés "assume-unchanged"**
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
> Voir [Ignorer (temporairement) des fichiers déjà trackés](#l2)

Editer fichier : ` .git/info/exclude `

**Modifier message du dernier commit**
> si pas déjà envoyé en ligne

`git commit --amend`  

**Modifier auteur du dernier commit**  
> si pas déjà envoyé en ligne  

`git commit --amend --author "username <email>"`  

**Nettoyer le répertoire de travail et l'index**
> Les modifications non commit seront perdues
`git reset --hard`

**Retourner à un ancien commit**  
`git checkout [id_commit]`

**Retourner au dernier commit**  
`git checkout master`

## Procédures

**Remisage**  
[Source](https://git-scm.com/book/fr/v1/Utilitaires-Git-Le-remisage)
> Permet de mettre de côté les modifications effectuées mais non commitées.
> Peut servir le temps de soumettre une correction en urgence

Pour créer une nouvelle remise sur votre pile, exécutez `git stash`  ou mieux   
`git stash save -u 'Message descriptif pour retrouver le stash'`  
Votre répertoire de travail est propre :
```sh
$ git status
# On branch master
nothing to commit, working directory clean
```
Pour voir quelles remises vous avez sauvegardées, vous pouvez utiliser la commande `git stash list`
```sh
$ git stash list
stash@{0}: WIP on master: 049d078 added the index file
stash@{1}: WIP on master: c264051... Revert "added file_size"
stash@{2}: WIP on master: 21d80a5... added number to log
```
Appliquer une remise `git stash apply stash@{2}`
> Utiliser l'option --index pour demander à Git d'essayer de réappliquer les modifications de votre index. Ex : `git stash apply stash@{2} --index`

Supprimer une remise
```sh
git stash drop stash@{0}
```

Appliquer et supprimer immédiatement la remise de votre pile
```sh
git stash pop stash@{0}
```

# Sources
 - [Git-attitude.fr - Options git qui gagnent à être connues](http://www.git-attitude.fr/2014/09/15/30-options-git-qui-gagnent-a-etre-connues/#stasher-plus%20efficacement%20avec%20save%20et%20-u)

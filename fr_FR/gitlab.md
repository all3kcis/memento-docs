# Gitlab
[Gitlab](https://about.gitlab.com/)  
Gitlab est une application web permettant de gérer des dépots Git.
## Fichiers de configuration
`/etc/gitlab/gitlab.rb`  
`/var/opt/gitlab/gitlab-rails/etc/gitlab.yml`  

A executer après modification du fichier de configuration
```sh
gitlab-ctl reconfigure
```

## Sauvegarde
```sh
gitlab-rake gitlab:backup:create
```
Le backup sera stocké dans `/var/opt/gitlab/backups`

## Restauration
@TODO
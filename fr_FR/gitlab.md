# Gitlab
[Gitlab](https://about.gitlab.com/)  
Gitlab est une application web permettant de gérer des dépots Git.

## Installation avec choix de version
```sh
apt-get update
apt-get install gitlab-ce=<YOUR-LATEST-MINOR-VERSION>-ce.0 # Ex : 13.1.1
gitlab-ctl reconfigure
gitlab-ctl restart
```
[Liste versions](https://packages.gitlab.com/gitlab/gitlab-ce)  
  
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

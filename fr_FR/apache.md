# Apache

## Fichiers de configurations
*php.ini*  
`/etc/php5/apache2/php.ini`  
@Todo

## Modules

### Voir les modules actifs
`apache2ctl -M`  
 > Liste des modules dans `/etc/apache2/mods-available/`

### Activer mod_headers
`a2enmod headers`

## Serveur

### Test configuration
`apachectl configtest`

### Relancer  
`service apache2 restart` Ou `/etc/init.d/apache2 restart`

# Docker

## Backup / Restore MongoDB
**Docker - dump**  
`docker exec <mongodb container> sh -c 'mongodump --archive' > db.dump`  
**Docker - restore**  
`docker exec -i <mongodb container> sh -c 'mongorestore --archive' < db.dump`  
**Docker-compose - dump**  
`docker-compose exec -T <mongodb service> sh -c 'mongodump --archive' > db.dump`  
**Docker-compose - restore**  
`docker-compose exec -T <mongodb service> sh -c 'mongorestore --archive' < db.dump`  

## Docker network
Exemple de création de réseau  
`docker network create --driver bridge networkname_netbit --subnet 174.100.0.0/16 --gateway 174.100.0.1 --opt com.docker.network.bridge.name=networkname`


## Gestion
`docker system df` permet de connaitre l’utilisation de l’espace disque.  
```
TYPE                TOTAL               ACTIVE              SIZE                RECLAIMABLE
Images              75                  1                   5.969GB             5.903GB (98%)
Containers          1                   1                   0B                  0B
Local Volumes       1                   0                   0B                  0B
Build Cache         0                   0                   0B                  0B
```
utiliser `docker system prune -a -f` pour nettoyer

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

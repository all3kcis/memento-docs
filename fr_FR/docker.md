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

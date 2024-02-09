Open the docker with mongo image
```sh
docker run -d -p 27017:27017 --restart=always --name mongo mongo:5.0.17 --replSet myReplicaSet --bind_ip_all
```

Initialize mongo sharding
```sh
docker exec mongo bash -c "mongosh --eval 'rs.initiate()'"
```

Copy file to docker
```sh
docker cp ~/Downloads/202310191047/cloudBar mongo:/tmp/.
```

Restore database to docker
```sh
docker exec -it mongo mongorestore --db cloudBar --verbose /tmp/cloudBar --drop
```

# solace-haproxy-sample

```
docker build -t dmrhaproxy .
docker run -d --network solace-net  -p 8108:8008 -p 8180:8080 -p 51555:55555 --shm-size=2g --env username_admin_globalaccesslevel=admin --env username_admin_password=admin --env system_scaling_maxconnectioncount=1000 --name=dmr1 solace/solace-pubsub-standard
docker run -d --network solace-net  -p 8208:8008 -p 8280:8080 -p 52555:55555 --shm-size=2g --env username_admin_globalaccesslevel=admin --env username_admin_password=admin --env system_scaling_maxconnectioncount=1000 --name=dmr2 solace/solace-pubsub-standard
docker run -d  --network solace-net  -p 8008:8008 -p 8080:8080 -p 55555:55555 --env ADMIN_USERNAME=admin --env ADMIN_PASSWORD=admin  --name=dmrlb dmrhaproxy:latest
```

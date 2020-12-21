# Docker:

> find container with filer name and the process running inside the container

```
docker container ls --filter name=istio-proxy_productpage* -q

docker container top $(docker container ls --filter name=istio-proxy_productpage* -q)

```

> login into a container

```
docker container ls --filter name=k8s_sleep
id=$(docker container ls --filter name=k8s_sleep --format '{{ .ID}}’)
docker container exec -it $id sh

docker container exec -it $(docker container ls --filter name=istio-proxy_productpage --format '{{ .ID}}') sh
```

> Test load on the network from a Fortio container from the local host machine.

```
docker container run --add-host "bookinfo.local:10.0.0.157" fortio/fortio load -c 32 -qps 25 -t 30s http://bookinfo.local/productpage
```

```
docker service create --name ruthgx -p 8080:80 --replicas 5 nginx
docker service ls
docker service stop ruthgx
docker service rm ruthgx
docker service create --name ruthgx -p 8080:80 --replicas 5 nginx
docker service ls
docker service ps ruthgx
docker service inspect ruthgx
docker swarm join-token manager

docker service scale ruthgx=5
docker service ps ruthgx
docker service update --replicas 10 ruthgx
docker network ls
docker service rm ruthgx
docker service ls
docker network create -d overlay ntwrk1
docker service create --name ruthgxx --network ntwrk1 -p 80:80 nginx
docker service inspect --pretty ruthgx
docker service create --name vote -p 8080:80 --network ntwrk1 --replicas 12 nigelpoulton/tu-demo:v1
docker service update --image nigelpoulton/tu-demo:v2 --update-parallelism 2 --update-dely 10s vote

~cd /var/lib/docker/
has info about containers, images, volumes etc……..
 
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
stop all containers [-a=all -q=quietly send only containers ID to output]
 
docker rmi $( docker images -q)
docker run -it –name ruth nginx:latest /bin/bash
docker run -d –name ruth -p 80:8080 nginx
```

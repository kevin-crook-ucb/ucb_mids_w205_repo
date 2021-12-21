# Instructions for Labs for Week 05

## Lab: Docker Compose - Single Container Cluster

Each Docker cluster has its own directory.  In each directory is a file docker-compose.yml.  Here is an example of single container cluster:

```
cd ~/docker/clusters/anaconda
```
Review docker-compose.yml

Check for stray containers:
```
docker ps -a
```
Startup our Docker cluster.  Note that we must be in the directory that contains the docker-compose.yml file for any command that starts with docker-compose.
```
docker-compose up -d
```

Check that the cluster came up (Note that there is no -a option with docker-compose):
```
docker-compose ps

docker ps -a
```
To exec a bash shell into a container (Note that we can run other programs besides bash):
```
docker-compose exec anaconda bash
```
Check the linux virtual console (aka "logs") for the container:
```
docker-compose logs anaconda
```
See the network:
```
docker network ls
```
Shutdown (aka "tear down") the cluster:
```
docker-compose down
```
Verify the cluster is down cleanly with no stray containers nor stray networks:
```
docker-compose ps

docker ps -a

docker network ls
```

## Lab: Docker Compose - Stray Cluster and Stray Network Cleanup

When running a cluster, there are several ways we can get a stray container or stray network:
* In a multi-container cluster, a container crashes and the other containers are still running
* We run multiple clusters and there is a resource conflict between them which prevents some containers from booting, while other containers boot
* We stop a container that is part of a cluster (accident?)
* We shutdown a cluster with the wrong docker-compose.yml file which is unable to stop all containers
* We stop the VM while a cluster is running

To detect stray containers in a cluster:
```
docker-compose ps

docker ps -a
```
If we see that a container in a cluster is not working, first try the cluster shutdown, as that would be the cleanest solution:
```
docker-compose down
```
Recheck for stray containers.  If any are found, we should remove them like this:
```
docker rm container_name
```
If the container does not respond, try a forced removal:
```
docker rm -f container_name
```
Now check for stray networks:
```
docker network ls
```
Three default networks are always present:
```
NETWORK ID     NAME      DRIVER    SCOPE
22eac0bb47bb   bridge    bridge    local
834615db7a14   host      host      local
3d4dfa7cfb57   none      null      local
```
Try to first prune any stray networks:
```
docker network prune
```
If that does not work, then as a last resort, remove the network:
```
docker network rm network_name
```

## Lab: Docker Compose - Two Container Clusters

Here are the two container clusters:
```
cd ~/docker/clusters/anaconda_mongo

cd ~/docker/clusters/anaconda_neo4j

cd ~/docker/clusters/anaconda_postgres

cd ~/docker/clusters/anaconda_redis
```
Use the same commands we previously learn to start the cluster, verify it's running, verify the network, exec a bash shell into the containers, shutdown the cluster, verify it came down cleanly:
```
docker ps -a

docker network ls

docker-compose up -d

docker-compose ps

docker-compose exec xxxx bash

docker-compose logs xxxx

docker-compose down
```

## Lab: Docker Compose - Networking in a Cluster Environment

Review the networking parameters in the various docker-compose.yml files:
```
cd ~/docker/clusters/anaconda

cd ~/docker/clusters/anaconda_kafka_zookeeper

cd ~/docker/clusters/anaconda_mongo

cd ~/docker/clusters/anaconda_neo4j

cd ~/docker/clusters/anaconda_postgres

cd ~/docker/clusters/anaconda_postgres_neo4j

cd ~/docker/clusters/anaconda_postgres_redis

cd ~/docker/clusters/anaconda_postgres_redis_nginx

cd ~/docker/clusters/anaconda_redis
```

## Lab: Docker Compose - Multiple Container Clusters with Networking


Here are the multiple container clusters (more than 2 containers):
```
cd ~/docker/clusters/anaconda_kafka_zookeeper

cd ~/docker/clusters/anaconda_postgres_neo4j

cd ~/docker/clusters/anaconda_postgres_redis

cd ~/docker/clusters/anaconda_postgres_redis_nginx
```

Use the same commands we previously learn to start the cluster, verify it's running, verify the network, exec a bash shell into the containers, shutdown the cluster, verify it came down cleanly:

```
docker ps -a

docker network ls

docker-compose up -d

docker-compose ps

docker-compose exec xxxx bash

docker-compose logs xxxx

docker-compose down
```


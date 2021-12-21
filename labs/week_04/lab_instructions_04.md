# Instructions for Labs for Week 04

## Lab: Docker - Creating Containers

This week focuses on Docker containers outside of clusters.  Next week, we will focus on Docker clusters.  Once you see Docker clusters, you will want to use them instead of single containers, however, we need to learn single containers first so we can understand clusters.  

List containers (does NOT list stray containers):
```
docker ps
```
List containers (includes stray containers):
```
docker ps -a
```
List Docker networks:
```
docker network ls
```
These 3 networks are always there by default:
```
NETWORK ID     NAME      DRIVER    SCOPE
22eac0bb47bb   bridge    bridge    local
834615db7a14   host      host      local
3d4dfa7cfb57   none      null      local
```
Create a container from the official Anaconda image.  
* -it => i means to redirect standard input from the VM's bash shell to the container's bash shell; t means create a pseudoterminal to replace standard output
* --rm => means to remove the container when we exit the bash shell (prevents stray containers)
* continuumio is the Docker Hub repo name; just like GitHub has repos, Docker Hub has repos
* anaconda3 is the image name
* latest is the version; omitting a version defaults to latest
```
docker run -it --rm continuumio/anaconda3:latest bash
```

## Lab: Docker - Stray Container Cleanup

Normally we won't get stray containers unless something goes wrong, such as shutting down the VM without shutting down Docker containers first, or an abend on Linux in the container.  In this example, we will create stray containers on purpose, so we can see how to detect and clean them up.

See if we have any stray containers (remember -a includes stray containers):
```
docker ps -a
```
Create a container without the --rm option.  When we exit the bash shell, we will be left with a stray container:
```
docker run -it continuumio/anaconda3:latest bash
```
To remove a container, we can remove them using either the container id or the container name:
```
docker rm container_id

docker rm container_name
```
If a container will not remove, such as a running container that won't shutdown, we can force it with the -f option.  Forcing a remove should always be a last resort, as it can corrupt mounted file systems:
```
docker rm -f container_id

docker rm -f container_name
```

## Lab: Docker - Persistence, Directory Mounting to Containers

Suppose we have a physical computer.  We create files on that computer.  Suppose we completely destroy the computer.  We lose those files.

We create containers.  We destroy containers.  It's the equivalent of destroying a computer.

Suppose we plug an external hard drive into a physical computer.  We can read files from the external hard drive.  We can write files to the external hard drive.  Suppose we destroy the computer, but keep the external hard drive.  We can plug the external hard drive into another computer and read the files, so we don't lose them.

We can create containers with a mounted external directory.  The mounted external directory works similar to an external hard drive.  We can read files from the mounted external directory.  We can write files to the mounted external directory.  When we destroy the container, the files on the external directory will survive and can be accessed from the VM, and can be mounted to other containers we create.
```
docker run -it --rm continuumio/anaconda3:latest bash

docker run -it --rm -v /home/w205/user:/user continuumio/anaconda3:latest bash
```

## Lab: Docker - Exposing and Mapping Ports in Containers

In most cases we run TCP/IP, the protocal that runs the Internet.  We are already familiar with IP addresses from AWS.  IP addresses route us to a physical computer or VM.  Once we get to the VM, a TCP port number is used to map us to a specific process.  Think of a "TCP port" as a "TCP address".  It's not a physical port, just a name for an address.  

When we run Docker, things on the VM get a bit more complicated.  We have to tell Docker which TCP ports to allow connections from the VM.  Since we can have TCP port conflicts, it allows us to map a port to another port number.

Expose will allow another Docker container to connect using the port number.  -p (ports) will allow the VM, and by extension external to the VM, to connect.  -p also allow us to remap a port number if we have conflicts. Note the first port is external, followed by a colon, then the remap port:
```
docker run -it --rm --expose 8888 -p 8888:8888 continuumio/anaconda3:latest bash

docker run -it --rm --expose 8888 -p 9999:8888 continuumio/anaconda3:latest bash
```

## Lab: Docker - Stray Network Cleanup

We have seen that Docker provides 3 networks by default:
```
docker network ls

NETWORK ID     NAME      DRIVER    SCOPE
22eac0bb47bb   bridge    bridge    local
834615db7a14   host      host      local
3d4dfa7cfb57   none      null      local
```
When we create a Docker container, it will use the bridge network by default.  We can create and use our own network, typically of type bridge (network types is a very complicated subject we won't cover here).  
```
docker network create -d bridge my_network
```
Start a container and tell it to use this network:
```
docker run -it --rm --network=my_network continuumio/anaconda3:latest bash
```
Prune networks that are not in use:
```
docker network prune
```
If prune does not work, we can force remove the network (only as a last resort!):
```
docker network rm my_network
```

## Lab: Docker - Microservices

In the concepts, we covered how originally services were huge due to technology limitations, but now with more modern tecnology, it's technologically feasible to have smaller and smaller services, to the point of microservices.

We also covered how corruption is worse than a crash. We covered the example of a cell phone starting to exhibit quirky behavior, we reboot it, and it works fine again.

We also covered business cases were we created a container for each individual user upon login, kept each user in their own container for the duration of the login, and destroyed the container upon logout.

Up until now, we have been running the bash shell when we create a container.  We can actually run any program.  

The following example: creates a Docker container, run the find program, exits, and destroys the container:
```
docker run -it --rm continuumio/anaconda3:latest find /var/log
```

## Lab: Docker - Creating an Image

List all images:
```
docker images
```

Each Docker image we are using for this course is custom build from a standard Docker image.  Each image has a directory.  The directory hold a Dockerfile, plus any files that we need to copy into the image:
```
cd ~/docker/images/w205_anaconda

cd ~/docker/images/w205_kafka

cd ~/docker/images/w205_mongo

cd ~/docker/images/w205_neo4j

cd ~/docker/images/w205_nginx

cd ~/docker/images/w205_postgres

cd ~/docker/images/w205_redis

cd ~/docker/images/w205_zookeeper
```

**Warning - you may just want to watch the video for creating images if this is new for you, as a lot can go wrong with image building.  Or, as an alternative, create a second VM, try this in the second VM, and then delete the second VM.**


To remove an image:
```
docker image rm xxxxx
```

Remove all images (be careful):
```
docker image rm $(docker images -aq)
```

To rebuild the custom images for this course:
```
cd ~/docker/images/w205_anaconda
docker build -t w205_anaconda .

cd ~/docker/images/w205_kafka
docker build -t w205_kafka .

cd ~/docker/images/w205_mongo
docker build -t w205_mongo .

cd ~/docker/images/w205_neo4j
docker build -t w205_neo4j .

cd ~/docker/images/w205_nginx
docker build -t w205_nginx .

cd ~/docker/images/w205_postgres
docker build -t w205_postgres .

cd ~/docker/images/w205_redis
docker build -t w205_redis .

cd ~/docker/images/w205_zookeeper
docker build -t w205_zookeeper .
```

## Lab: Docker - Examples of How Various Official Images are Built

Docker Hub - stores the Docker images in the format: docker_hub_repo_name/image_name/version_name

To create these Docker images, the source code, including Dockerfile and any files that will be copied in are typically stored in a GitHub repo.  It should always be possible to clone down the GitHub repo and build any image from scratch.

Here are some example official images we can take a look at:

**Anaconda**

https://hub.docker.com/r/continuumio/anaconda3

https://github.com/ContinuumIO/docker-images

**Postgres**

https://hub.docker.com/_/postgres

https://github.com/docker-library/postgres

**Neo4j**

https://hub.docker.com/_/neo4j

https://github.com/neo4j/docker-neo4j

**Mongo**

https://hub.docker.com/_/mongo

https://github.com/docker-library/mongo

**Redis**

https://hub.docker.com/_/redis

https://github.com/docker-library/redis

**Kafka**

https://hub.docker.com/r/confluentinc/cp-kafka/

https://github.com/confluentinc/kafka-images

**Zookeeper**

https://hub.docker.com/r/confluentinc/cp-zookeeper

Same GitHub repo as Kafka above

**NGINX**

https://hub.docker.com/_/nginx

https://github.com/nginxinc/docker-nginx

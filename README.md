### My Docker Installation and Configuration Process

#### docker version
returns the version of docker on our machine

#### docker info
returns the complete info about docker engine. eg. complete configuration, engine info, all image info etc.

docker

docker container run

docker run

### Starting a Nginx Web Server

#### docker container run --publish 80:80 nginx
spinup the server on localhost - it might take few minutes to install dependencies first time. goto browser and hit localhost

ctrl + c to type detach commands
#### docker container run --publish 80:80 --detach nginx
detach tells docker to run in background. and get new unique id for container. 

#### docker container ls
shows all file and dir inside container

#### docker container stop a0593
type few strating keys from unique id to stop that particular container. 

#### docker container ls
it will show current running container we stopped our container so it won't show anything 

#### docker container ls -a
each time we run container it creates new unique id and store info about that container eg. default username, when created, its unique id etc.

#### docker container run --publish 80:80 --detach --name webhost nginx
creating a new instance using user-name 
Note: If we dont specify name it takes something random 

#### docker container ls -a
list all the container 

#### docker container start id
to start that particular user container

#### docker container logs webhost
show logs for specific container. latest logs for webhost user

#### docker container top
it requires atleast 1 argument.. for more detail we can see using command `docker container top --help`

#### docker container top webhost
process running inside the container. we can see all running process

#### docker container --help
we can see all commands we can execute on that particular container

#### docker container ls -a
list all my containers

#### docker container rm df5 a05 b5b
this will remove all 3 containers which I created. 
**Note:** It wont remove any running container so before removing running container we first need to stop that container. and if you do you will get something like this `Error response from daemon: You cannot remove a running container df5f1247393f78b9226d3aa5a7e5d0093c041fce6ea78740629587ca772c2bc9. Stop the container before attempting removal or force remove`

#### docker container ls
to see running container

#### docker container rm -f 63f
either we can stop that container or remove it forcefully by using `-f` flag. as I did in this command. 

#### docker container ls -a
list all my container. (I wont get any bcs I already deleted all my container)


### Container VS. VM: It's Just a Process

docker run --name mongo -d mongo

docker ps

docker top mongo

docker stop mongo

docker ps

docker top mongo

docker start mongo

docker ps

docker top mongo


## What's Going On In Containers: CLI Process Monitoring

docker container run -d --name nginx nginx

docker container run -d --name mysql -e MYSQL_RANDOM_ROOT_PASSWORD=true mysql

docker container ls

docker container top mysql

docker container top nginx

docker container inspect mysql

docker container stats --help

docker container stats

docker container ls

## Getting a Shell Inside Containers: No Need for SSH

docker container run -help

docker container run -it --name proxy nginx bash

docker container ls

docker container ls -a

docker container run -it --name ubuntu ubuntu

docker container ls

docker container ls -a

docker container start --help

docker container start -ai ubuntu

docker container exec --help

docker container exec -it mysql bash

docker container ls

docker pull alpine

docker image ls

docker container run -it alpine bash

docker container run -it alpine sh

## Docker Networks: Concepts for Private and Public Comms in Containers

docker container run -p 80:80 --name webhost -d nginx

docker container port webhost

docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost

## Docker Networks: CLI Management of Virtual Networks

docker network ls

docker network inspect bridge

docker network ls

docker network create my_app_net

docker network ls

docker network create --help

docker container run -d --name new_nginx --network my_app_net nginx

docker network inspect my_app_net

docker network --help

docker network connect

docker container inspect TAB COMPLETION

docker container disconnect TAB COMPLETION

docker container inspect

## Docker Networks: DNS and How Containers Find Each Other

docker container ls

docker network inspect TAB COMPLETION

docker container run -d --name my_nginx --network my_app_net nginx

docker container inspect TAB COMPLETION

docker container exec -it my_nginx ping new_nginx

docker container exec -it new_nginx ping my_nginx

docker network ls

docker container create --help


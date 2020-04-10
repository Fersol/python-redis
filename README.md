# python-redis
Test task for docker swarm

##  Where to play
https://labs.play-with-docker.com

## references
https://docs.docker.com/engine/swarm/stack-deploy/

## Download
git clone https://github.com/Fersol/python-redis

## Create swarm 

docker swarm init  --advertise-addr 192.168.0.48

To add workers: run this at node to add (this command will be shown after docker swarm init)

docker swarm join --token SWMTKN-1-3n4r4i8e129divjs9coewg4rezifucdk7mkx3i9c330qc5zy81-2w2rm3i6hr3z65588umjtb28w 192.168.0.48:2377

Check worker connection

docker node ls

## Up service from docker-compose.yml in swarm
docker stack --orchestrator swarm deploy -c docker-compose.yml my_service

Check that all is working

docker node ps

docker service ps my_service_web

Check app status

curl 192.168.0.8:80

## Delete service
docker stack rm my_service


### Build docker image for app
login in DockerHub

docker login

Build image for app from Dockerfile

docker build -t fersol/python-redis:v3 .

Send image to Dockerhub

docker push fersol/python-redis:v3

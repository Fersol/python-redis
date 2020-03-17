# python-redis
Test task for docker swarm

# based on
https://docs.docker.com/engine/swarm/stack-deploy/

# Download via curl
curl -LOk https://github.com/Fersol/python-redis/archive/master.zip
curl -LkSs https://github.com/Fersol/python-redis/tarball -o master.tar.gz

# Create swarm
docker swarm init  --advertise-addr 192.168.0.48

# add members
Такая штука появляется в предыдущей команде, ее надо юзать
docker swarm join --token SWMTKN-1-3n4r4i8e129divjs9coewg4rezifucdk7mkx3i9c330qc5zy81-2w2rm3i6hr3z65588umjtb28w 192.168.0.48:2377

Проверить, что ноды подключились
docker node ls

# Скачать свой код
git clone https://github.com/Fersol/python-redis

# Сначала нужно собрать все образа
docker-compose build

# Проверить образы
docker images

# Меняем образ в compose

# Поднять из docker-compose.yml файла систему
docker stack --orchestrator swarm deploy -c docker-compose.yml my_service

docker ps
# Чекнуть, что работает
curl 192.168.0.8:5000

docker node ps
docker service ls

# Удалить сервис 
docker stack rm my_service




# Делаем свой репозиторий в хабе
docker build -t fersol/python-redis:v3 .
Когда уже есть докерфайл
ПОтом делаем
docker push fersol/python-redis:v3
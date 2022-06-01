docker version - базовая инфа
docker info - больше инфы 

docker container run --publish 80:80 nginx - запустит контейнер с nginx. Можно написать http://localhost/ в браузере и увидеть home page.
docker container run --publish 80:80 --detach n
ginx - флаг detach скажет запустить докер в бекграунде.
docker container run --publish 80:80 --detach --name *name* nginx - флаг name позволяет указывать имя контейнера вместо смешных пр умолчанию
80:80 первая 80 это порт локальной машины, вторая 80 это порт на контейнере. Указав это мы преадрессует трафик с локальной машины на контейнер.

docker stop *глупое название контейнера или container id*
docker 

docker removal rm *ids через пробел* - удаляет выелюченные контейнеры. (Безопасно)
docker removal rm -f *ids через пробел* - удаляет нафиг все контейнеры

docker container ls -a - просмотр списка всех контейнеров.

docker container logs *название контейнера*
docker container top - просмотр процессов контейнера

docker container -- help

Разница между контейнером и виртуальной машиной. Контейнер это просто процесс. 
Его можно просмотреть внутри контейнеа через docker container top так и просто на локальной машине, через команду показывающую процессы.

docker network ls 


docker container top - process list in one container
docker container inspect - details of one container config
docker container stats - performance stats for all containers

docker container run -it - start new container interactively (где t - нужен для ssh подключения из терминала, а i - чтобы мы могли выполнить команды внутри контейнера и он не закрылся после первой)
docker container exec -it - run additional command in existing container












  docker network create app-tier --driver bridge
  docker run -d --name zookeeper-server --network app-tier -e ALLOW_ANONYMOUS_LOGIN=yes bitnami/zookeeper:latest
  docker run -d --name kafka-server --network app-tier -p 9092:9092 -e ALLOW_PLAINTEXT_LISTENER=yes -e KAFKA_CFG_ADVERTISED_LISTENERS=PLAINTEXT://127.0.0.1:9092 -e KAFKA_CFG_ZOOKEEPER_CONNECT=zookeeper-server:2181 bitnami/kafka:latest

   kafka-topics.sh --create --replication-factor 1 --partitions 1 --bootstrap-server kafka-server:9092 -topic topicname
   kafka-console-producer.sh --broker-list localhost:9092 --topic topicname
   kafka-console-consumer.sh  --bootstrap-server localhost:9092 --topic topicname --from-beginning


# docker-mautic
Para construir la imagen, docker compose
```
$ docker-compose build
```

Para arrancar Mautic, ejecutar el siguiente comando:
```
$ docker-compose up -d
```

Acceder a phpMyAdmin con un navegador a http://localhost:8082
Acceder a Mautic con un navegador a http://localhost:8083

```
 Stop all container
    docker kill $(docker ps -q)
$ docker exec -it bash

```
Ver network
$ docker network ls
& docker network inspect mautic-net

# Crear Docker
$ docker volume create mysql_data

$ docker run --name percona -d \
    -p 3306:3306 \
    -e MYSQL_ROOT_PASSWORD=12345678 \
    -v mysql_data:/var/lib/mysql \
    percona/percona-server:5.7 \
     --character-set-server=utf8mb4 --collation-server=utf8mb4_general_ci


     $ docker volume create mautic_data

$ docker run --name mautic -d \
    --restart=always \
    -e MAUTIC_DB_HOST=127.0.0.1 \
    -e MAUTIC_DB_USER=root \
    -e MAUTIC_DB_PASSWORD=12345678 \
    -e MAUTIC_DB_NAME=mautic \
    -e MAUTIC_RUN_CRON_JOBS=true \
    -e MAUTIC_TRUSTED_PROXIES=0.0.0.0/0 \
    -p 8080:80 \
    -v mautic_data:/var/www/html \
    mautic/mautic:latest


# redis-rpi

This is a docker-compose service for a standalone Redis server for RPi.
(It should also be worked at Linux box)

## Installation
1. Copy the file: `dotenv.sample` to `.env` and modify the values as necessary

## Start the (daemon) service
Change to the project directory and type:
```
$ docker-compose up -d
```
Please note that docker-compose will use that folder name as the project name.  

## Alternate project name
You may specify an alternate project name:
```
$ docker-compose -p my-project up -d
```
or
```
$ export COMPOSE_PROJECT_NAME=my-project && \
docker-compose up -d
```

However, you may get trouble to use docker-compose command after.  For example, you cannot view the processes by:
```
$ docker-compose ps
```
but this:
```
$ docker-compose -p my-project ps
```

Therefore, by copying this project folder to another project folder may save you from trouble.

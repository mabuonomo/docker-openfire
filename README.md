# docker-compose openfire

This docker setup contains a stack with:
* openfire v4.4.0

## Official image on Docker Hub
https://cloud.docker.com/repository/docker/sharksoft/openfire

## Quickstart
Start only Openfire server using:

```bash
$ docker-compose up -f docker-compose.yml
```

Start full stack Openfire/MySQL using:

```bash
$ docker-compose up
```

## Services
* Openfire Admin Console > http://localhost:9090 

## Openfire connect to MySQL
Use this db settings in openfire initial setup:
* jdbc:mysql://mysql_openfire:3306/openfire?rewriteBatchedStatements=true 
* user: openfire
* pwd: openfire

## Destroy Stack
```bash
$ docker-compose stop
$ docker-compose rm
$ docker system prune --force --volumes
```

## Based on
* https://github.com/sameersbn/docker-openfire
* https://github.com/juanromanf/openfire-stack
# docker-compose openfire

This docker setup contains a stack with:
* openfire v4.4.0

## Quickstart
Start Openfire using:

```bash
$ docker-compose up
```

## Services
* Openfire Admin Console > http://localhost:9090 

## Openfire
Use this db settings in openfire initial setup:
* jdbc:mysql://database_srv:3306/openfire_db?rewriteBatchedStatements=true 
* user: openfire
* pwd: openfire

## Destroy Stack
```bash
$ docker-compose stop
$ docker-compose rm
$ docker system prune --force --volumes
```
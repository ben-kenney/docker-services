# Introduction
gitea https://gitea.io is a self-hosted git server.

Out of the box, it doesn't support Jupyter notebook rendering and so mods must be made to the docker commands.

We need to install python and jupyter notebook via a Dockerfile and then make a custom config file "app.ini".

The config file is implemented via a mapped volume.

Instructions can be found in various places including the gitea help docs but I found that none of them really worked and the solution needed to be pieced together.

## First run
```
docker-compose up -d --build
```
Then run through the configuration files. Select postgres, and remember that the database location is refereced by db:5432. Also should change the domain to the IP address (or better domain name) of the server.

## Second run
```
docker-compose up -d
```
Something seems to go wrong when trying to build the Dockerfile again.

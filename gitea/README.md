# Introduction
gitea https://gitea.io is a self-hosted git server.

Out of the box, it doesn't support Jupyter notebook or asciidoctor rendering and so modifications must be made to the docker commands.

For jupyter support, we need to install python and jupyter notebook via a Dockerfile and then make a custom config file "app.ini".

The config file is implemented via a mapped volume.

Instructions can be found in various places including the gitea help docs but I found that none of them really worked and the solution needed to be pieced together.

The app.ini file is mapped to custom/conf/app.ini

The header.tpbl file is mapped to custom/templates/custom/header.tmpl


## First run
```
docker-compose up -d --build
```
Then configure the server. Select postgres, and remember that the database location is refereced through docker by db:5432. Also if this is self-hosted might want to change the domain to the IP address (or better domain name) of the server.

### Install

DB: psql://db:5432
DB username / password -> see docker-compose.yml
Host name: Replace all instances of localhost with either the machine name or the IP
Administration: Probably best practice is to create an admin user




## Second run
```
sudo docker-compose up -d
```
The ssh directory is owned by root and so we require sudo in case we need to rerun (after changing app.ini or Dockerfile for example).

## Config changes
It appears safe to update the dockerfile and the app.ini file after first use, *but* make sure to include all of the modifications that are made to app.ini upon installation.

## Backup
Still to be tested, but generally should be able to archive the entire gitea directory.

## Other thoughts
In production environment should experiment with putting the git repos on an external drive to make backup easier and also using nginx or traefik.

## Connecting to container
To connect to the gitea container, just use

```
docker exec -it gitea bash -c /bin/sh
```

note that gitea is that container name.

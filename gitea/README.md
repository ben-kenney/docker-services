# Introduction
gitea https://gitea.io is a self-hosted git server.

Out of the box, it doesn't support Jupyter notebook or asciidoctor rendering and so mods must be made to the docker commands.

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
sudo docker-compose up -d
```
The ssh directory is owned by root and so we require sudo in case we need to rerun (after changing app.ini or Dockerfile for example).

## Config changes
It appears safe to update the dockerfile and the app.ini file after first use, *but* make sure to include all of the modifications that are made to app.ini upon installation.

## Backup
Still to be tested, but generally should be able to archive the entire gitea directory.

## Other thoughts
In production environment should experiment with putting the git repos on an external drive to make backup easier.

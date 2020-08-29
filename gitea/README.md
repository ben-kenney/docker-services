# Introduction
gitea https://gitea.io is a self-hosted git server.

Out of the box, it doesn't support Jupyter notebook rendering and so mods must be made to the docker commands.

We need to install python and jupyter notebook via a Dockerfile and then make a custom config file "app.ini".

The config file is implemented via a mapped volume.

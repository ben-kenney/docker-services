# Introduction

To upgrade octoprint:

```
docker-compose down
```

Edit the docker-compose.yml file and update the version in ```octoprint/octoprint:1.5.3```, then:

```
docker-compose up -d --build
```
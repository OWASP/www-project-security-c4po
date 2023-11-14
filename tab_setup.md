---
title: Docker Setup
layout:  null
tab: true
order: 2
tags: c4po-docker-setup
---

## Docker Hub Setup
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)](https://hub.docker.com/repository/docker/cellecram/security-c4po/general)
* Pull all images:
    * `docker image pull --all-tags cellecram/security-c4po`
* Create network:
    * `docker network create -d bridge c4po`
* Start images:
    * `docker run --network=c4po --name c4po-keycloak -d -p 8080:8080 cellecram/security-c4po:keycloak`
    * `docker run --network=c4po --name c4po-db -d -p 27017:27017 cellecram/security-c4po:mongo`
    * `docker run --network=c4po --name c4po-angular -d -p 4200:4200 cellecram/security-c4po:angular`
    * `docker run --network=c4po -e "SPRING_PROFILES_ACTIVE=COMPOSE" --name c4po-api -d -p 8443:8443 cellecram/security-c4po:api`
    * `docker run --network=c4po -e "SPRING_PROFILES_ACTIVE=COMPOSE" --name c4po-reporting -d -p 8444:8444 cellecram/security-c4po:reporting`

### OR: Run Script (Docker Hub)
Execute `c4po-prod.sh` and all services will be pulled from Docker Hub and started.
You can reach the application by entering http://localhost:4200 in you browser.
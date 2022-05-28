---
title: How to install Portainer
date: 2022-05-23 20:00
categories: [homelab, docker]
tags: [portainer, docker]
---

# How to install Portainer
## What is Portainer?
Portainer is a GUI that can be hosted within a docker container that allows you to manage other docker containers with features such as 
* Starting and stopping sontainers.
* Creating Docker containers
* One click installs of popular containers
* Docker-compose creation
With both light and dark mode themes, Portainer is a great way to manage your containers. So heres how to install it.

## How to install Portainer on Ubuntu
### Prerequisites
* Docker 
* Docker Compose

### Commands
```bash
docker volume create portainer_data
```
Setup a volume for portainer to store its data 

```bash
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```
Installs Portainer into its own docker container and allows port 9000.

```bash
docker run -it --name portainer-database-rollback -v portainer_data:/data portainer/portainer-ee:latest --rollback-to-ce
```
Reverts back to the community edition of Portainer so that it can run correctly.
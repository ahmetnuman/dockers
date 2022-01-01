---
layout: post
title: Docker For Beginners
tags: Docker For Beginners
categories: docker
---

## **Objectives**

- What are Containers ?
- What is Docker ?
- Why do you need it ?
- What can it do ?
- Run Docker Containers
- Create a Docker Image
- Networks in Docker
- Docker Compose
- Docker Concepts in Depth
- Docker for Windows/Mac
- Docker Swarm
- Docker vs Kubernetes

---

## Why do we need docker ?

#### Classic deployment

![Image](/img/classical-app.png)

- Compatibility/Dependency
- Long setup time
- Different Dev/Test/Prod environments

#### Deployment with Docker

![Image](/img/docker-app.png)

- Containerize applications
- Run each service with its own dependencies in seperate containers 

#### What are containers ?

![Image](/img/whatareontainers.png)

- Containers are completely isolated environments.
- They can have their own 
  - process or services, 
  - network interfaces, 
  - mounts
- Containers working like virtual machines except they all share the same OS kernel
- There are different type of containers like LXC, LXD, LXCFS etc.
- Docker utilizes LXC containers setting up these container environments.   

#### Docker Editions

- Community Edition 
- Enterprise Edition

#### Docker Install on Ubuntu Server 20.04 Focal

- [Install Docker on Ubuntu](https://docs.docker.com/engine/install/ubuntu)


**Install docker with script**

```
 curl -fsSL https://test.docker.com -o test-docker.sh
 sudo sh test-docker.sh
```

![Image](/img/docker-script.png)

![Image](/img/run-script.png)


**Check version of running docker**

`sudo docker version`

![Image](/img/dockerersion.png)

**Run a Sample Container to verify everythink is working as expected**

- [Install whalesay container](https://hub.docker.com/r/docker/whalesay)

`sudo docker run docker/whalesay cowsay boo`

![Image](/img/dockerrun.png)
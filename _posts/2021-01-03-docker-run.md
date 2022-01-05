---
layout: post
title: Docker Run
tags: Docker Run
categories: docker
---

- **Run - tag**

`sudo docker run redis` --> This command will downlaod latest version of redis. When we want to download different version of redis we can use tag like below.

`sudo docker run redis:4.0`

---

- **Run - stdin**

Docker container by default promts does not to listen standart input.

`sudo docker run -i kodekloud/simple-prompt-docker` --> **-i means interactive**

`sudo docker run -it kodekloud/simple-prompt-docker` --> **-t means terminal**

---

- **Run - PORT Mapping**

`sudo docker run -p 80:5000 kodekloud/webapp` --> clients will be access with 80 port from out of the box

`sudo docker run -p 8000:5000 kodekloud/webapp`

`sudo docker run -p 8001:5000 kodekloud/webapp`

`sudo docker run -p 8002:5000 kodekloud/webapp`

`sudo docker run -p 3306:3306 kodekloud/webapp`

`sudo docker run -p 8306:3306 kodekloud/webapp`

---

- **Run - Volume Mapping**

`sudo docker run -v /opt/datadir:/var/lib/mysql mysql`

---

- **Inspect Container**

`sudo docker inspect blissful_hopper`

This command will list detail of information about the container config with json format.

---

- **Container Logs**

`sudo docker logs blissful_hopper`

---

```
sudo docker ps
sudo docker run ubuntu
sudo docker run ubuntu cat /etc/*release*
sudo docker run ubuntu:17.10 cat /etc/*release*

sudo docker run ubuntu sleep 15
sudo docker run -d ubuntu sleep 1000
sudo docker ps
sudo docker attach f13b
sudo docker stop f13b
sudo docker run timer
sudo docker run -d timer
sudo docker ps
sudo docker attach d090

sudo docker run jenkins/jenkins
sudo docker ps
sudo docker inspect eb85
(inside the same host : http://172.17.0.2:8080) (from the outside box 192.168.1.14:8080 will not listen , we have to use port mapping)
sudo docker run -p 8080:8080 jenkins/jenkins
(now we can access http://192.168.1.14:8080)
(install default plugins to jenkins then stop and start docker you will see al configuration will be deleted)
mkdir my-jenkins-data
sudo docker run -p 8080:8080 -v /home/anuman/my-jenkins-data:/var/jenkins_home -u root jenkins/jenkins

```


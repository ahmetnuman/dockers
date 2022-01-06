---
layout: post
title: Docker Images
tags: Docker Images
categories: docker
---

**How to create our docker image?**

I will containerized simple web app written by python flask.

1. OS - Ubuntu
2. Update apt repo
3. Install dependencies using apt
4. Instal Python dependencies using pip
5. Copy source code to /opt folder
6. Run the web server using "flask" command

Dockerfile according to previous this steps.

```
FROM Ubuntu
RUN apt-get update && apt-get -y install python
RUN pip install flask flask-mysql
COPY . /opt/source-code
ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```

Build docker image from this file with the docker build command

`sudo docker build . -f Dockerfile -t numan/my-custom-app`

Push the docker to docker image to make avaliable publicly

`sudo docker push ahmetnuman/my-custom-app`

---

#### Demo : Creating Docker Image

- [Application Source Code : https://github.com/mmumshad/simple-webapp-flask](https://github.com/mmumshad/simple-webapp-flask)

If we installed this app on the ubuntu container steps will be like this :


``` 
anuman@dockerlabs:~$ sudo docker run -it ubuntu bash
root@2532dfc67b33:/# apt-get update -y
root@2532dfc67b33:/# apt-get install python -y
root@2532dfc67b33:/# apt-get install python3-pip -y
root@2532dfc67b33:/# pip install flask
root@2532dfc67b33:/# FLASK_APP=app.py flask run --host=0.0.0.0
```

we can dockerize this simple app according to these commands

- `mkdir my-simple-webapp`
- `cd my-simple-webapp`
- `copy app.py codes in this directory`

**Dockerfile**

```
FROM ubuntu
RUN apt-get update
RUN apt-get install -y python python3-pip
RUN pip install flask
COPY app.py /opt/app.py
ENTRYPOINT FLASK_APP=/opt/app.py flask run --host=0.0.0.0
```

- `sudo docker build . `
- `sudo docker build . -t my-simple-web-app`
- `sudo docker images`
- `sudo docker run -d -p 5000:5000 my-simple-webapp`


**we can access web from out of the host now**

`curl -v <ip of the host>:5000`

**Pushing image to the docker hub**

- `sudo docker build -t 717717/mysimple-webapp`
- `sudo docker login`
- `sudo docker push 717717/my-simple-webapp`
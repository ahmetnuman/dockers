---
layout: post
title: Docker Images Lab
tags: Docker Images Lab
categories: docker
---

- **How many images are available on this host?**

`sudo docker images`

![Image](/img/images1.png)

---

- **What is the size of the ubuntu image?**

`sudo docker images`

![Image](/img/images2.png)

---

- **We just pulled a new image. What is the tag on the newly pulled NGINX image?**

![Image](/img/images3.png)

---

- **We just downloaded the code of an application. What is the base image used in the Dockerfile? Inspect the Dockerfile in the webapp-color directory.**

- `ls`
- `cd webapp-color`
- `ls`
- `cat Dockerfile`

![Image](/img/images4.png)

- **To what location within the container is the application code copied to during a Docker build? Inspect the Dockerfile in the webapp-color directory.**

- `ls`
- `cd webapp-color`
- `ls`
- `cat Dockerfile`

![Image](/img/images5.png)

---

- **When a container is created using the image built with this Dockerfile, what is the command used to RUN the application inside it.**

- `ls`
- `cd webapp-color`
- `ls`
- `cat Dockerfile`

![Image](/img/images6.png)

---

- **What port is the web application run within the container?**

- `ls`
- `cd webapp-color`
- `ls`
- `cat Dockerfile`

![Image](/img/images7.png)

---

- **Build a docker image using the Dockerfile and name it webapp-color. No tag to be specified.**

```
ls 
webapp-color
cd webapp-color/
ls   
Dockerfile  app.py  requirements.txt  templates
sudo docker build . -t webapp-color
```

![Image](/img/images8.png)

---

- **Run an instance of the image webapp-color and publish port 8080 on the container to 8282 on the host.**

`sudo docker run -p 8282:8080 webapp-color`

![Image](/img/images9.png)

---

- **Access the application by clicking on the tab named HOST:8282 above your terminal.**

![Image](/img/images10.png)

---

- **What is the base Operating System used by the python:3.6 image? If required, run an instance of the image to figure it out.**

`sudo docker run -d python:3.6 cat /etc/*release`

![Image](/img/images11.png)

---

- **What is the approximate size of the webapp-color image?**

`sudo docker images`

![Image](/img/images12.png)

---

- **That's really BIG for a Docker Image. Docker images are supposed to be small and light weight. Let us try to trim it down.**

- **Build a new smaller docker image by modifying the same Dockerfile and name it webapp-color and tag it lite. Find a smaller base image for python:3.6. Make sure the final image is less than 150MB.Modify Dockerfile to use python:3.6-alpine image and then build using docker build -t webapp-color:lite .**

Dockerfile :

```
FROM python:3.6-alpine
RUN pip install flask
COPY . /opt/
EXPOSE 8080
WORKDIR /opt
ENTRYPOINT ["python", "app.py"]
```

`sudo docker built . -t webapp-color:lite`

![Image](/img/images13.png)


---

- **Run an instance of the new image webapp-color:lite and publish port 8080 on the container to 8383 on the host.**

`sudo docker run -d -p 8383:8080 webapp-color:lite`

![Image](/img/images14.png)


































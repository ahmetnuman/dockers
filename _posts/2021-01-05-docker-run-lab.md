---
layout: post
title: Docker Run
tags: Docker Run
categories: docker
---

- **Let us first inspect the environment. How many containers are running on this host?**

`sudo docker ps`

![Image](/img/dokcerq1.png)

---

- **What is the image used by the container?**

`sudo docker ps`

![Image](/img/dokcerq2.png)

---

- **How many ports are published on this container?**

`sudo docker ps`

![Image](/img/dokcerq3.png)

---

- **Which of the below ports are the exposed on the CONTAINER?**

`sudo docker ps`

![Image](/img/dokcerq4.png)

---

- **Which of the below ports are published on Host?**

`sudo docker ps`

![Image](/img/dokcerq5.png)

---

- **Run an instance of kodekloud/simple-webapp with a tag blue and map port 8080 on the container to 38282 on the host.**

`sudo docker run -p 38282:8080 kodekloud/simple-webapp:blue`

![Image](/img/dokcerq6.png)

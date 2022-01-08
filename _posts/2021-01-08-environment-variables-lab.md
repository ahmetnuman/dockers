---
layout: post
title: Environment Variables Lab
tags: Environment Variables Lab
categories: docker
---

- **Inspect the environment variables set on the running container and identify the value set to the APP_COLOR variable.**

`sudo docker ps`
`sudo docker inspect 0ff`

![Image](/img/envlab1.png)

![Image](/img/envlab2.png)

![Image](/img/envlab3.png)

---

- **Run a container named blue-app using image kodekloud/simple-webapp and set the environment variable APP_COLOR to blue. Make the application available on port 38282 on the host. The application listens on port 8080.**

`sudo docker run -d -e APP_COLOR=blue --name=blue-app -p 38282:8080 kodekloud/simple-webapp`

![Image](/img/envlab4.png)

---

- **View the application by clicking the link HOST:38282 above your terminal and ensure it has the right color.**

![Image](/img/envlab5.png)

---

- **Deploy a mysql database using the mysql image and name it mysql-db. Set the database password to use db_pass123. Lookup the mysql image on Docker Hub and identify the correct environment variable to use for setting the root password.**


![Image](/img/envlab6.png)

`sudo docker run -d -e MYSQL_ROOT_PASSWORD=db_pass123 --name=mysql-db mysql`

![Image](/img/envlab7.png)


---
layout: post
title: CMD vs ENTRYPOINT Lab
tags: CMD vs ENTRYPOINT Lab
categories: docker
---

- **Dockerfiles for a few commonly used Docker Images are given in the /root (current) directory. Inspect them and try to answer the following questions.**

---

- **What is the ENTRYPOINT configured on the mysql image?**

`cat Dockerfile-mysql`

![Image](/img/entrylab1.png)

---

- **What is the CMD configured on the wordpress image?**

`cat Dockerfile-wordpress`

![Image](/img/entrylab2.png)

---

- **What is the final command run at startup when the wordpress image is run. Consider both ENTRYPOINT and CMD instructions**

`cat Dockerfile-wordpress`

![Image](/img/entrylab3.png)

---

- **What is the command run at startup when the ubuntu image is run?**

`cat Dockerfile-ubuntu`

![Image](/img/entrylab4.png)

---

- **Run an instance of the ubuntu image to run the sleep 1000 command at startup.**

`sudo docker run -d ubuntu sleep 1000`





---
layout: post
title: CMD vs ENTRYPOINT
tags: CMD vs ENTRYPOINT
categories: docker
---

**if we run simple ubuntu container on the docker, it will start ubuntu container then exit from it immediately.**

`sudo docker run ubuntu`
`sudo docker ps`
`sudo docker ps -a`

![Image](/img/entry1.png)

**Examine nginx, mysql and ubuntu docker file and attend the CMD line**

![Image](/img/entry2.png)

![Image](/img/entry3.png)

**when we run the ubuntu image bash command couldnt find to anythink then it stopped the service immediately**

---

**How do you specify a different command to start the container?**

- **once option is to append a command to the docker run command and that way it overrides the default command**

- `sudo docker run ubuntu [COMMAND]`
- `sudo docker run ubuntu sleep 5`

- **How do you make that change permenantly? We can create docker file and specify CMD**

- **Dockerfile:**

```
FROM ubuntu
CMD sleep 5
```

![Image](/img/entry4.png)

![Image](/img/entry5.png)

---

**We can specify command with the JSON file format**

- `CMD ["command", "param1"]`
- `CMD ["sleep", "5"]`

**What if i wish to change the number of seconds it sleeps currently ? We can use append command like `sudo docker run sleeper sleep 10` but in this way this commands doesnt look very good. We only want to pass in the number of seconds the container should sleep automatically like this `sudo docker run ubuntu-sleeper 10`. That is where entry point comes into play.**

```
FROM ubuntu
ENTRYPOINT ["sleep"]
```

- **default entry point parameter**

```
FROM ubuntu
ENTRYPOINT ["sleep"]
CMD ["5"]  ---> defult entry point parameter
``` 
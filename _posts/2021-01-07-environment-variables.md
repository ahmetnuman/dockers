---
layout: post
title: Environment Variables
tags: Environment Variables
categories: docker
---

**app.py code without Environment Variables**

- [Applicaition Repository](https://github.com/mmumshad/simple-webapp-color)


```
import os
from flask import Flask
from flask import render_template
import socket
import random
import os

app = Flask(__name__)

color_codes = {
    "red": "#e74c3c",
    "green": "#16a085",
    "blue": "#2980b9",
    "blue2": "#30336b",
    "pink": "#be2edd",
    "darkblue": "#130f40",
    "yellow":"#FFFF00"
}

color = "red"

@app.route("/")
def main():
    #return 'Hello'
    print(color)
    return render_template('hello.html', name=socket.gethostname(), color=color_codes[color])

if __name__ == "__main__":
    app.run(host="0.0.0.0", port="8080")
```

**run app**

`sudo python3 app.py`

**view app**

![Image](/img/viewapp.png)

---

**app.py code with Environment Variables**

```
import os
from flask import Flask
from flask import render_template
import socket
import random
import os

app = Flask(__name__)

color_codes = {
    "red": "#e74c3c",
    "green": "#16a085",
    "blue": "#2980b9",
    "blue2": "#30336b",
    "pink": "#be2edd",
    "darkblue": "#130f40",
    "yellow":"#FFFF00"
}

color = os.environ.get('APP_COLOR')

@app.route("/")
def main():
    #return 'Hello'
    print(color)
    return render_template('hello.html', name=socket.gethostname(), color=color_codes[color])

if __name__ == "__main__":
    app.run(host="0.0.0.0", port="8080")
```

**run app with environment variable**

`export APP_COLOR=blue; python3 app.py`

![Image](/img/viewapp1.png)


`export APP_COLOR=red; python3 app.py`

![Image](/img/viewapp2.png)

---

**Now dockerize this application**

**Dockerfile**

```
FROM ubuntu
RUN apt-get update -y
RUN apt-get install python -y
RUN apt-get install python3-pip -y
RUN pip install flask
RUN mkdir /opt/source-code
RUN mkdir /opt/source-code/templates
COPY app.py /opt/source-code/app.py
COPY templates/hello.html /opt/source-code/templates/hello.html
ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run --host=0.0.0.0
```

`sudo docker build . -t simple-webapp-color`

**run docker image wit environment variables**

- `sudo docker run -d -e APP_COLOR=blue  -p 5000:5000 simple-webapp-color`
- `sudo docker run -d -e APP_COLOR=green -p 5001:5000 simple-webapp-color`
- `sudo docker run -d -e APP_COLOR=pink  -p 5002:5000 simple-webapp-color`


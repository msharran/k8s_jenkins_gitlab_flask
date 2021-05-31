# flask-demo (Hello World)
---
Please run `start` script to run the Flask server:
```bash
./start
```
---
# Dockerized flask-demo (Hello World)
 
Please start docker to run the Flask server as container:
```bash
docker build -t flaskdemo .
docker run -it -p 4000:4000 flaskdemo
```
---

**NOTE:** I have pushed the image in my DockerHub Repository for kubernetes to pull the image while running

https://hub.docker.com/r/sharran/flaskdemo



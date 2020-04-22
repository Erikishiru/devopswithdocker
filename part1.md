## 1.1 Getting Started
```
$ docker ps -a 
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS               NAMES
04bffe133667        nginx               "nginx -g 'daemon of…"   3 minutes ago       Up 2 minutes               80/tcp              wonderful_herschel
33bdfdb8a1ce        nginx               "nginx -g 'daemon of…"   3 minutes ago       Exited (0) 2 minutes ago                       optimistic_liskov
d0f1cbefefbc        nginx               "nginx -g 'daemon of…"   3 minutes ago       Exited (0) 2 minutes ago                       magical_shaw
```
## 1.2 Cleanup 
```
$ docker ps -as 
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS               NAMES                SIZE
04bffe133667        nginx               "nginx -g 'daemon of…"   3 minutes ago       Up 2 minutes               80/tcp              wonderful_herschel   2B (virtual 127MB)
33bdfdb8a1ce        nginx               "nginx -g 'daemon of…"   3 minutes ago       Exited (0) 2 minutes ago                       optimistic_liskov    0B (virtual 127MB)
d0f1cbefefbc        nginx               "nginx -g 'daemon of…"   3 minutes ago       Exited (0) 2 minutes ago                       magical_shaw         0B (virtual 127MB)
```
```
$ docker images 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              5a8dfb2ca731        26 hours ago        127MB
```
After Cleanup
```
$ docker ps -a 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
$ docker images 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```

## 1.3 Hello Docker Hub
Secret message is:
"This is the secret message"

Commands used 
```
$ docker run -it devopsdockeruh/pull_exercise
Unable to find image 'devopsdockeruh/pull_exercise:latest' locally
latest: Pulling from devopsdockeruh/pull_exercise
8e402f1a9c57: Pull complete 
5e2195587d10: Pull complete 
6f595b2fc66d: Pull complete 
165f32bf4e94: Pull complete 
67c4f504c224: Pull complete 
Digest: sha256:7c0635934049afb9ca0481fb6a58b16100f990a0d62c8665b9cfb5c9ada8a99f
Status: Downloaded newer image for devopsdockeruh/pull_exercise:latest
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```

## 1.4 
Secret message is:
"Docker is easy"

Commands used 
```
$ docker pull devopsdockeruh/exec_bash_exercise
```
```
$ docker run -d --rm -it --name ex1_4 devopsdockeruh/exec_bash_exercise 
```
```
$ docker exec -it ex1_4 bash 
root@531c810bc716:/usr/app# tail -f ./logs.txt
"Docker is easy"
Fri, 17 Apr 2020 13:59:06 GMT
Fri, 17 Apr 2020 13:59:09 GMT
Fri, 17 Apr 2020 13:59:12 GMT
Fri, 17 Apr 2020 13:59:15 GMT
Secret message is:
"Docker is easy"
```

## 1.5
To start the process 
```
$ docker run -it --name helsinkifi ubuntu:16.04 sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
```

To fix the ensuing problems.
```
$ docker run -d --rm -it --name helsinkifi ubuntu:16.04 sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
```
```
$ docker exec -it helsinkifi bash
root@fc0f1b4fe478:/# apt install curl
```

## 1.6
[Dockerfile](https://github.com/Erikishiru/devopswithdocker/blob/master/exercise1-6/Dockerfile)

Command used to run the container 
```
$ docker run docker-clock
```

## 1.7
[Dockerfile](https://github.com/Erikishiru/devopswithdocker/blob/master/exercise1-7/Dockerfile)

Command used to run the container 
```
$ docker run -it curler 
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
```
## 1.8
```
$ docker pull devopsdockeruh/first_volume_exercise
$ touch logs.txt
$ docker run -v $(pwd)/logs.txt:/usr/app/logs.txt --name log devopsdockeruh/first_volume_exercise
```

## 1.9
```
$ docker run -d -p 80 devopsdockeruh/ports_exercise
3152f5e43b90e5e8065707f2df2d05f9a401ad3065be42b5014f1105eeb4b76c
$ docker port 3152
80/tcp -> 0.0.0.0:32769
```

## 1.10
[Dockerfile](https://github.com/Erikishiru/devopswithdocker/blob/master/exercise1-10/Dockerfile)

## 1.11
[Dockerfile](https://github.com/Erikishiru/devopswithdocker/blob/master/exercise1-11/Dockerfile)

Commands used 
```
$ docker build -t backend .
$ docker run -d -p 8000:8000 -v $(pwd)/logs.txt:/backend-example-docker/logs.txt backend
```

## 1.12
[Frontend Dockerfile](https://github.com/Erikishiru/devopswithdocker/blob/master/exercise1-12/frontend/Dockerfile)

[Backend Dockerfile](https://github.com/Erikishiru/devopswithdocker/blob/master/exercise1-12/backend/Dockerfile)

Commands used 
```
$ docker run -d -p 5000:5000 frontend 
$ docker run -d -p 8000:8000 backend
```

## 1.13 
[Dockerfile](https://github.com/Erikishiru/devopswithdocker/blob/master/exercise1-13/Dockerfile)

## 1.14
[Dockerfile](https://github.com/Erikishiru/devopswithdocker/blob/master/exercise1-14/Dockerfile)

## 1.15 
[Docker Hub Image](https://hub.docker.com/repository/docker/erikishiru/flaskapp)

## 1.16
[Application URL](https://devopsdocker-heroku.herokuapp.com/)

## 1.17
[Docker Hub Image for devenvreact](https://hub.docker.com/repository/docker/erikishiru/devenvreact)

This is a development environment to create a new react app inside a docker container.

To run the container run the following command
```
$ docker run -it -d -v $(pwd):/react -p 3000:3000 devenvreact
```

Open the my-app direcotry in any code editor to develop an application inside a container.
 Part 1
## 1.1 Getting Started
```
$ docker ps -a 
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS               NAMES
04bffe133667        nginx               "nginx -g 'daemon of…"   3 minutes ago             Up 2 minutes               80/tcp              wonderful_herschel
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
```
$ docker stop 04
04
$ docker rm 04
04
$ docker rm 33
33
$ docker rm d0 
d0
$ docker rmi 5a 
Untagged: nginx:latest
Untagged: nginx@sha256:4d947aef8841aed19cc0896a38e12d49d50feba7f583998a164ffeb31e655919
Deleted: sha256:5a8dfb2ca7312ee39433331b11d92f45bb19d7809f7c0ff19e1d01a2c131e959
Deleted: sha256:eede83f79a434879440e1f6f6f98a135b38057a35ddcdace715ae1bddcd7a884
Deleted: sha256:fa994cfd7aeedcd46b70cf30fea0ccf9f59f990bbb86bfa9b7c02d7ff2a833eb
Deleted: sha256:b60e5c3bcef2f42ec42648b3acf7baf6de1fa780ca16d9180f3b4a3f266fe7bc
```
```
$ docker ps -a 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
$ docker images 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```

## 1.3 Hello Docker Hub
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
### Terminal Window 1
```
$ docker pull devopsdockeruh/exec_bash_exercise
Using default tag: latest
latest: Pulling from devopsdockeruh/exec_bash_exercise
741437d97401: Pull complete 
34d8874714d7: Pull complete 
0a108aa26679: Pull complete 
7f0334c36886: Pull complete 
65c95cb8b3be: Pull complete 
a36b708560f8: Pull complete 
4090f912e6c7: Pull complete 
ce5fe2607c2e: Pull complete 
9400f5f657d6: Pull complete 
c4919883f7fa: Pull complete 
Digest: sha256:c463832132d1fb0b8b3b60348a6fc36fda7512a4ef2d1050e8bea7b6a6d7a2f3
Status: Downloaded newer image for devopsdockeruh/exec_bash_exercise:latest
docker.io/devopsdockeruh/exec_bash_exercise:latest
$ docker run -d --rm -it --name ex1_4 devopsdockeruh/exec_bash_exercise 
531c810bc716dbb074d441759995fc22b669b9b44611753c6dfad01669931052
```
### Ternianl Window 2
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
Fri, 17 Apr 2020 13:59:21 GMT
Fri, 17 Apr 2020 13:59:24 GMT
^C
root@531c810bc716:/usr/app# exit 
exit
$ docker kill ex1_4
ex1_4
$ docker container ls 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
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
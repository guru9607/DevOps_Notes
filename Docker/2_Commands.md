## Commands
1) Become root user
```
$ sudo su  --> Use to become root user
```
2) Installing docker
```
$ yum update -y
$ yum install docker -y
```
3) Checking Docker version,
```
$ docker -v
$ docker --version
Docker version 20.10.24, build 297e128
```
4) Checking docker path
```
$ which docker 
/usr/bin/docker
```
5) Starting docker
```
$ service docker start 
```
6) Checking Docker is running or not
```
$ service docker status
$ docker info
```
---

7) Create and run the docker image
- -it means interactive terminal
- ubuntu is the name of the image
```
# docker run -it ubuntu /bin/bash

Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
29202e855b20: Pull complete 
Digest: sha256:e6173d4dc55e76b87c4af8db8821b1feae4146dd47341e4d431118c7dd060a74
Status: Downloaded newer image for ubuntu:latest
```
You will be inside the container. If you check which OS it is,
```
$ cat /etc/os-release
.
NAME="Ubuntu"
.
.
```
If you want to exit it,
```
$ exit --> now your container will not be in running state
```
---
8) Search an image
```
$ docker search ubuntu
Here ubuntu is the name of the image
```
9) List all the Docker images that are currently downloaded on your system.
```
$ docker images

REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
ubuntu       latest    e34e831650c1   2 weeks ago   77.9MB
```

**Note:** When you run ubuntu image again new container will be created with new id. <br>
Example: (it includes naming the container as well)
```
$ docker run -it --name guruprasad ubuntu /bin/bash
guruprasad => name that i want to give to the container.
```

10) Check containers status
```
$ docker ps ==> for running containers
$ docker ps -a ==> for all containers

Now, if you do
$ docker ps -a ==> you will get list of containers in which newly created one will be on top.

CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                        PORTS     NAMES
3316fba82ea7   ubuntu    "/bin/bash"              9 seconds ago    Exited (0) 5 seconds ago                guruprasad
82e5bca68186   ubuntu    "--name Guruprasad /…"   12 minutes ago   Created                                 nifty_hodgkin
```

11) Start docker which you exited
```
$ docker start guruprasad
```

12) To go inside container
```
$ docker attach guruprasad
```
13) To stop the container
```
$ docker stop guruprasad
```
14) Remove
```
$ docker rm guruprasad ==> The one which is not in active condition can be removed
```



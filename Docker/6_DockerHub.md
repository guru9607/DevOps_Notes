# DockerHub
```
$ sudo su      # Graha pravesh
$ yum update -y
$ yum install docker -y
$ service docker start
$ docker run -id ubuntu /bin/bash

NOTE: 1) -td (t -> terminal, d -> daemon)
      2) -p (port or publish)
      3) 80 : 80 (Host : Container)

$ docker ps
$ docker port techserver     # Gives details about containers ports being mapped with host.
O/p => 80/TCP  => 0.0.0.0/80

$ docker exec -it techserver /bin/bash

NOTE: We use exec instad of attach here

$ apt-get update
$ apt-get install apache2
$ cd /var/www/html
$ echo "Guruprasad Gaikwad" > index.html
$ service apache2 start
$ docker run -td --name myjenkins -p 8080:8080 jenkins
```
2) Now, create some files iniside container
3) Createv images in the container
```
$ docker commit container1 image1
```
4) Now, create account on `hub.docker.com`
5) Now, go to EC2 instance

```
$ docker login
Enter the username and password
```
6) Give tag to your imag
```
$ docker tag image <docker_id>/<any_tag_name>
$ docker push <docker_id>/<any_tag_name>
```

7) Now, you can see the image in docker hub account
8) Create one instance from tokyo and pull the image
```
$ docker pull <docker_id>/<any_tag_name>
$ docker run -it --name mycontainer <docker_id>/<any_tag_name> /bin/bash
```

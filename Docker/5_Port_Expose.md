# Steps

- Login into AWS account, create one linux instance
- Now, go to putty -> login as -> ec2-user

```
$ sudo su      # Graha pravesh
$ yum update -y
$ yum install docker -y
$ service docker start
$ docker run -td --name techserver -p 80:80 ubuntu

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

- Abhi agar ham <HOST_IP>:8080 dalenge to hame google se voh access kar payenge, security group mai 8080 expose hona chaiyye
- Apache ke liye <HOST_NAME>:80 dalne ki no need,<HOST_NAME> se kaam chal jayega kyoki voh default port hai http ka.

---

#### Theory
**1) Difference between exec and attach?** <br>
`docker exec`: Adds new processes to a running container. <br>
`docker attach`: Connects your terminal to the main process inside a container.

**Hindi** <br>
Docker exec (Chalu container ka naya termial) <br>
Docker attach (Chalu container ka existing terminal) 

**2) Diff between Expose and publish command?** <br>
Basically you have 3 options: 
1)	Neither specify expose nor P. 
2)	Only specify expose.
3)	Specify exposed and -p

---
- If you specify neither `expose` nor `-p`, the service in the container will only be accessible from inside the container itself.
- If you `expose` a port, the service in the container is not accessible from outside the doctor but from inside other docker containers so this is good for inter container communication 
- If you `expose` and `-p` a port, the service in the container is accessible from anywhere, even outside the docker. <br>
- If you do `-p` Yeah. but do not expose, docker does an implicit expose. This is because if a port is open to the public, it is automatically also opened to the other docker container. Hence P includes EXPOSE.

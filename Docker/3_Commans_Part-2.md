Till now we studied how to create container using image from docker hub, now we will learn how to create container using our **own images**🚀

Suppose you created EC2 instance, and run the ubuntu image,
```
$ docker run -it --name guruprasad ubuntu /bin/bash 
```
Now do the following,
```
$ cd tmp/
$ touch myfile1.txt
```
We if you want to see the difference between base image and changes in it
```
docker diff guruprasad
guruprasad => Name of container

C /root
A /root/.bash_history
C /tmp  
A /tmp/myfile.txt
```
Here,
C => changes, 
A => Append, Addition, 
D => Deletion

How to create image of this container?
```
$ docker commit guruprasad updateimage
```
Hurray!! New Image created 🥳

Now, lets create container from updateimage, 
```
$ docker run -it --name guruprasad2 updateimage /bin/bash
```




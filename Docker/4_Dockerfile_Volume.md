# Dockerfile
- Dockerfile is basically a text file which contains some set of instruction.
- It helps us in automation of docker image creation.
## Commands
1. **FROM**: Specifies the base image for your Docker image. Example: `FROM ubuntu`
2. **RUN**: Executes commands in the shell of the container during the build process. Create a layer in image Example: `RUN apt-get update && apt-get install -y python`
3. **Maintainer**: Author/Owner/Description. 
4. **COPY**: Copies files or directories from the host machine into the container's filesystem. We need to provide source and destination. (We cannot download anything from internet). Example: `COPY . /app`
5. **ADD**: Similar to COPY, but with additional features like unpacking compressed files, downloading files from internet. Example: `ADD app.tar.gz /app`
6. **WORKDIR**: Sets the working directory inside the container for subsequent commands. Example: `WORKDIR /app`
7. **EXPOSE**: Exposes ports on the container to allow communication with the outside world. Example: `EXPOSE 8080`
8. **ENV**: Sets environment variables inside the container. Example: `ENV APP_ENV=production`
9. **CMD**: Specifies the default command to run when the container starts. Example: `CMD ["python", "app.py"]`
10. **ENTRYPOINT**: Similar to CMD but more priority. Example: `ENTRYPOINT ["java", "-jar", "app.jar"]`
11. **ARG**: Set values that might change between different builds or that you want users to be able to customize without modifying the Dockerfile directly.

## Procedure
1) Create a file named Dockerfile
```
$ vi Dockerfile
```
2) Add instruction to dockerfile
```
$ FROM ubuntu
$ RUN echo "Guruprasad Gaikwad" > /tmp/testfile      # test file banao touch command se
```
3) Build dockerfile to create image
```
$docker build -t myimg .
---
-t stands for tag , image ko naam dene ke liye and "." means use Dockerfile of current Directory.
Now, to check whether image is created or not
---
$ docker ps -a
$ docker image
```
4) To create container from the above image
```
$ docker run -it --name mycontainer myimg /bin/bash
$ cat /tmp/testfile
```
#### Example 2
```
vi Dockerfile
FROM ubuntu
WORKDIR /tmp
RUN echo "Hello🙌❤️" > /tmp/testfile1
ENV myname guruprasadgaikwad
COPY testfile1 /tmp
ADD test.tar.gz /tmp
```
How to create this zip file?
```
$ touch test
$ tar -cvf test.tar test
$ gzip test.tar
```

# Docker Volume
- Volume is simply a directory inside our container. Firstly, we have to declare the directory as a volume and then share volume.
- Volumes can be directories or data stored on the host filesystem, managed by Docker. 
- Even if we stop container, still we can access volume.
- Volume will be created in one container. 
- You can declare a directory as a volume only while creating container.
- You can't create volume from existing container.
- You can share one volume across any number of containers.
- Volume will not be included when you update an image. i.e. Agar ek container mai volume banaya, usse ek image banayi and then uss image se ek aur container banaya, then it will not include the volume. 
- You can map volume in 2 ways.
    1. Container <--> container
    2. Host <--> container

### Benefits
1) Decoupling Storage and Containers
2) Sharing Data Among Containers
3) Easy Attachment of Volumes
4) On deleting container volume is not deleted.

## Procedure
1) Create a file named Dockerfile
```
$ vi Dockerfile
```
2) Add instruction to dockerfile
```
$ FROM ubuntu
$ VOLUME ["/myvolume1"]
```
3) Build dockerfile to create image
```
$docker build -t myimg .
```
4) To create and run container from the above image
```
$ docker run -it --name container1 myimg /bin/bash
```
Agar create and run alag alag karna ho to?
```
$ docker create --name <container_name> <img_name>
$ docker start <container_name>
```
5) Sharing with other containers Container <--> Container
```
$ docker run -it --name container2 --privileged=true --volumes-from container1 myimg /bin/bash
```
Now, after creating container2 whaterver you do in one volume, you can see in other volume
```
$ touch /myvolume1/simplefile
$ docker start container1
$ docker attach container1
```

#### Creating volume by using command
1) 
```
docker run -it --name container3 -v /volume2 ubuntu /bin/bash
```
2) Now, create one file constainer3file and exit
3) Create one more container, and share volume2
```
docker run -it --name container4 --priviledged=true --volume-from container3 ubuntu /bin/bash
```
4) Now you are inside container and if we ls, we can see volume2
5) Now, create one dfile inside the volume and then check in container3 you can see that file.

## Volume (Host <--> Container)
1) Verify files in /home/ec2-user
```
$ docker run -it --name hostcontainer -v /home/ec2-user:/newvolume ubuntu /bin/bash
$ cd /newvolume
```
2) Do ls, now you can see all files of host machine
```
$ touch testfile (in container)
$ exit
```
3) Now check ec2 machine, you can see this file

## Other Popular Commands
```
$ docker volume ls (list all volume created locally)
$ docker volume create <volumename>
$ docker volume rm <volumename>
$ docker volume prune  {remove all unused docker volume}
$ docker volume inspect <volumename>
$ docker container inspect <containername>
```

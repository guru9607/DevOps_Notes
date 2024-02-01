# Docker

- Docker is an open-source centralized platform designed to create, deploy, and run applications.
- Docker uses containers on the host operating system to run applications. It allows applications to use the same Linux kernel as the system on the host computer rather than creating a whole virtual OS.
'''
Containers?
A container is a bundle of Application, Application libraries required to run your application and the minimum system dependencies.
'''
- Docker can be installed on any OS, but the Docker engine runs natively on Linux distributions.
- Docker is written in Go language.
- Docker is a tool that performs OS-level virtualization, also known as containerization.
- Before Docker, many users faced the problem that a particular code was running on the developer's system but not on the user's system.
- Docker was first released in March 2013. It was developed by Solomon Hykes and Sebastian Pahl.
- Docker is a set of platform as a service that uses OS-level virtualization, whereas VMware uses hardware-level virtualization.

## Containers vs Virtual Machine 
Containers and virtual machines are both technologies used to isolate applications and their dependencies, but they have some key differences:

    1. Resource Utilization: Containers share the host operating system kernel, making them lighter and faster than VMs. VMs have a full-fledged OS and hypervisor, making them more resource-intensive.
    2. Portability: Containers are designed to be portable and can run on any system with a compatible host operating system. VMs are less portable as they need a compatible hypervisor to run.
    3. Security: VMs provide a higher level of security as each VM has its own operating system and can be isolated from the host and other VMs. Containers provide less isolation, as they share the host operating system.
    4. Management: Managing containers is typically easier than managing VMs, as containers are designed to be lightweight and fast-moving.


## Advantages:

1) No free allocation of RAM.
2) CI efficiency → Docker enables you to build a container image and use that same image across every step of the deployment process.
3) Less cost.
4) It is lightweight.
5) It can run on physical hardware/virtual hardware.
6) You can reuse the image.

## Limitations:

- Docker is not a good solution for applications that require a rich GUI.
- Difficult to manage a large number of containers.
- Docker does not provide cross-platform compatibility, meaning if an application is designed to run in a Docker container on Windows, then it can't run on Linux or vice versa.
- Docker is suitable when the development OS and testing OS are the same; if the OS is different, we should use VM.
- No solution for data recovery and backup.

## Docker Architecture
![title](Images/Architecture.jpeg)


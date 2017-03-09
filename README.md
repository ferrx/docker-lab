# IOP Docker Lab
Examples and Instructions for IOP Docker Lab

## Install Docker Toolbox for Windows
Download and install [Docker Toolbox](https://github.com/docker/toolbox/releases/download/v1.12.5/DockerToolbox-1.12.5.exe). If there are any issues during installation, see [the installation guide](https://docs.docker.com/toolbox/toolbox_install_windows/#step-2-install-docker-toolbox).

Once installed, you should have "Docker Quickstart" available on your desktop. Open this to generate a virtual machine called "default" (aka docker-machine).

Once the "default" docker-machine has been created, you can use it at any point from Docker Quickstart, CMD, or PowerShell.

## Docker Toolbox Basics
Docker Toolbox can be used on older flavors of Windows and uses VirtualBox to create Linux-based Virtual Machines (aka docker-machine) to run Docker Linux Containers. If you have Windows 10 Pro (or higher), you have access to "Docker for Windows" which runs natively without the need for a VM, and can run both Linux Containers and Windows Containers.

+ To use your Docker Toolbox environment in CMD or PowerShell, open a shell window and use "docker-machine env <name-of-VM>". For example, "docker-machine env default" will setup the "default" docker-machine environment in this shell window.

+ Once your environment is setup, you can access docker commands such as "docker images", "docker ps" etc.

+ To get the IP for your docker-machine, use "docker-machine ip <name-of-VM>".

## Common Docker Commands
+ To **get a list of images** use `docker images`
+ To **pull an image** from DockerHub use `docker pull <user-name>\<image-name>:<tag-name>`
+ To **build an image** use `docker build -t <image-name> .` within a directory with a Dockerfile
+ To **push an image** to DockerHub use `docker push <user-name>\<image-name>:<tag-name>`
+ To **remove an image** from your machine use `docker rmi <image-name>`
+ To **create a container** use `docker run --name <container-name> <image-name>`
+ To **view a list of running containers** use `docker ps`
+ To **view a list of running and stopped containers** use `docker ps -a`
+ To **stop a running container** use `docker stop <container-name>`
+ To **start a stopped container** use `docker start <container-name>`
+ To **remove a stopped container** use `docker rm <container-name>`
+ To **remove a running container** use `docker rm <container-name> -f`
+ To **remove all containers** use `powershell docker rm $(docker ps -a -q) -f`
+ To **execute a command on a running container** use `docker exec <container-name> <command>`
+ To **enter a running a container with PowerShell** use `docker exec -it <container-name> powershell`

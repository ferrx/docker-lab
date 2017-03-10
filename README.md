# IOP Docker Lab
Examples and Instructions for IOP Docker Lab
![Docker](https://securityledger.com/wp-content/uploads/2015/05/docker-1024x347.png)

## Docker Basics
Docker provides virtualization technology that has fast start-up times and small resource footprint. Docker containers achieve this efficiency by sharing the host's kernel. This is contrary to a virtual machine which requires its own kernel. Eliminating the kernel and all of its necessary resources means that the virtualized operating system can be much smaller and processes required for kernel-level services do not need to be spun up.

<p align="center"><img src="https://image.slidesharecdn.com/developerweek2015-docker-tutorial-150209173058-conversion-gate02/95/developerweek-2015-a-practical-introduction-to-docker-6-638.jpg?cb=1423503745" /></p>

### Docker Images and Containers.
+ Docker Images are used to create Containers based on the specification within the image
+ Containers run your applications, act as your web server, your database server, etc

### Dockerfile
Images are built using a `Dockerfile` which is a plain text file that specifies to Docker what the image should consist of, such as:
+ The base image, i.e. `debian:jessie`, `microsoft/nanoserver` or another Docker image (think of it as a chain of inheritance)
+ Bootstrap commands executed when the container starts up, such as installing an apache web server, installing php, enabling Windows features, and much more
+ Files to copy into the image
+ Ports to be exposed, for example you might want port 80 exposed for any containers acting as a webserver

Example Dockerfile (from [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/))
```
FROM microsoft/dotnet:1.0-runtime-deps

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        curl \
    && rm -rf /var/lib/apt/lists/*

# Install .NET Core
ENV DOTNET_VERSION 1.0.4
ENV DOTNET_DOWNLOAD_URL https://dotnetcli.blob.core.windows.net/dotnet/preview/Binaries/$DOTNET_VERSION/dotnet-debian-x64.$DOTNET_VERSION.tar.gz

RUN curl -SL $DOTNET_DOWNLOAD_URL --output dotnet.tar.gz \
    && mkdir -p /usr/share/dotnet \
    && tar -zxf dotnet.tar.gz -C /usr/share/dotnet \
    && rm dotnet.tar.gz \
    && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet
```

### Docker Compose
Docker Compose is a tool that can be used to generate a full stack of containers using a single `docker-compose.yml` file that defines your stack. For example, you may have a Dockerfile for an Apache webserver and another Dockerfile for a PHP web application. You can use Docker Compose to create both containers at once, as well as tying together any dependencies and resources that each might need.

### Docker Hub
[Docker Hub](https://hub.docker.com) is Docker's public ecosystem that acts as a repository for Docker Images. Here you can find images such as PHP, MySQL, IIS, ASP.Net, DotNetCore, and thousands more, for pulling down and using in your docker environment.

## Install Docker Toolbox for Windows
Download and install [Docker Toolbox](https://github.com/docker/toolbox/releases/download/v1.12.5/DockerToolbox-1.12.5.exe). If there are any issues during installation, see [the installation guide](https://docs.docker.com/toolbox/toolbox_install_windows/#step-2-install-docker-toolbox).

Once installed, you should have "Docker Quickstart" available on your desktop. Open this to generate a virtual machine called "default" (aka docker-machine).

Once the "default" docker-machine has been created, you can use it at any point from Docker Quickstart, CMD, or PowerShell.

## Docker Toolbox Basics
Docker Toolbox can be used on older flavors of Windows and uses VirtualBox to create Linux-based Virtual Machines (aka docker-machine) to run Docker Linux Containers. If you have Windows 10 Pro (or higher), you have access to "Docker for Windows" which runs natively without the need for a VM, and can run both Linux Containers and Windows Containers.

To see a list of docker-machine VMs in your environment use `docker-machine ls`

To use your Docker Toolbox environment in CMD or PowerShell perform the following:
+ Open a shell window and use `docker-machine env <docker-machine-name>`
+ Run the following command to set variables: `@FOR /f "tokens=*" %i IN ('docker-machine env <docker-machine-name>') DO @%i`

Once your environment is setup, you can access docker commands such as `docker images`, `docker ps` etc.

To get the IP for your docker-machine, use `docker-machine ip <docker-machine-name>`.

## Common Docker Commands
### Managing Images
+ To **get a list of installed images** use `docker images`
+ To **build an image** use `docker build -t <image-name> .` within a directory with a Dockerfile
+ To **pull an image** from DockerHub use `docker pull <user-name>/<image-name>:<tag-name>`
+ To **push an image** to DockerHub use `docker push <user-name>/<image-name>:<tag-name>`
+ To **remove an image** from your machine use `docker rmi <image-name>`

### Managing Containers
+ To **create a container** use `docker run --name <container-name> <image-name>`
+ To **create a container that will run in the background** use `docker run -d <image-name>`
+ To **create a container that maps a host:guest port** use `docker run -p <host-port>:<guest-port> <image-name>`
+ To **view a list of running containers** use `docker ps`
+ To **view a list of running and stopped containers** use `docker ps -a`
+ To **stop a running container** use `docker stop <container-name>`
+ To **start a stopped container** use `docker start <container-name>`
+ To **remove a stopped container** use `docker rm <container-name>`
+ To **remove a running container** use `docker rm <container-name> -f`
+ To **remove all exited containers** use `powershell docker rm $(docker ps -af status=exited -q)`
+ To **remove all containers** use `powershell docker rm $(docker ps -a -q) -f`
+ To **view container properties** use `docker inspect <container-name>`

### Interacting with Containers
+ To **execute a command on a running container** use `docker exec <container-name> <command>`
+ To **enter a running a container with bash** use `docker exec -it <container-name> bash`

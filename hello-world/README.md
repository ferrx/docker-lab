# Your First Docker Container

This installation will use the hello-world and ubuntu images.
For more on the hello-world image, view its image on Docker Hub [here](https://hub.docker.com/_/hello-world/).
For more on the ubuntu image, view its image on Docker Hub [here](https://hub.docker.com/_/ubuntu/).

To pull the `hello-world` image from Docker Hub, use the following in your terminal:
```
docker pull hello-world:latest
```

To start a container from that image:
```
docker run --name my-first-container hello-world
```

To see my-first-container after it has stopped:
```
docker ps -a
```

To remove my-first-container:
```
docker rm my-first-container
```

To remove the hello-world image:
```
docker rmi hello-world
```

To interact with a container using bash:
```
docker run -it ubuntu bash
```

To interact with a running container:
```
docker run -itd --name my-ubuntu ubuntu
docker exec -it my-ubuntu bash
```

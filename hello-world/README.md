# Your First Docker Container

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
docker exec -it ubuntu bash
```

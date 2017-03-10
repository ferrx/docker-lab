# Create an Apache HTTPd Server

<p align="center"><img src="http://crasstalk.com/wp-content/uploads/2013/05/Apache-Web-Server.png" /></p>

> The Apache HTTP Server, colloquially called Apache (/əˈpætʃiː/ ə-PA-chee), is the world's most used web server software. Originally based on the NCSA HTTPd server, development of Apache began in early 1995 after work on the NCSA code stalled.

This installation uses the HTTPd image. For more information about this image, view its image on Docker Hub [here](https://hub.docker.com/_/httpd/).

### Create a Dockerfile
On your local computer, create a file called `Dockerfile` with the following content:
```
FROM httpd:2.4
RUN echo "Hello World From Apache HTTPd!" > /usr/local/apache2/htdocs/index.html
```

### Build your image
From your terminal, navigate to the folder with your `Dockerfile` and perform the following command:
```
docker build -t httpd-server .
```

### Run your container
From your terminal, create a new container that uses your image using the following command:
```
docker run -d -p 8090:80 --name mysite httpd-server
```
You should now be able to access your site on port 8090. To get the IP, use `docker-machine ip <docker-machine-name>` in your terminal.

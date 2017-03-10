# Create an Apache HTTPD Server

<p align="center"><img src="http://crasstalk.com/wp-content/uploads/2013/05/Apache-Web-Server.png" /></p>

> The Apache HTTP Server, colloquially called Apache (/əˈpætʃiː/ ə-PA-chee), is the world's most used web server software. Originally based on the NCSA HTTPd server, development of Apache began in early 1995 after work on the NCSA code stalled.

This installation uses the Apache HTTPD image. For more information about this image, view its image on Docker Hub [here](https://hub.docker.com/_/httpd/).

### Create a Dockerfile
```
FROM httpd:2.4
RUN echo "Hello World From Apache HTTPD!" > /usr/local/apache2/htdocs/index.html
```

### Build your image
```
docker build -t httpd-server .
```

### Run your container
```
docker run -d -p 8090:80 --name mysite httpd-server
```

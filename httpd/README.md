# Create an Apache HTTPD Server

```
FROM httpd:2.4
RUN echo "Hello World From Apache HTTPD!" > /usr/local/apache2/htdocs/index.html
```

```
docker build -t httpd-server .
```

```
docker run -d -p 8090:80 --name mysite httpd-server
```

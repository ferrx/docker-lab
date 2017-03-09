### Install WordPress Using Docker

<p align="center"><img src="https://s.w.org/about/images/logos/wordpress-logo-stacked-rgb.png" /></p>

> Blurb

For more information about this image, see [WordPress on Docker Hub](https://hub.docker.com/_/wordpress/).

Create a Docker Compose file called `docker-compose.yml` and add the following:
```
version: '2'

services:

  wordpress:
    image: wordpress
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_PASSWORD: example

  mysql:
    image: mariadb
    environment:
      MYSQL_ROOT_PASSWORD: example
```

Within that directory, perform the following Docker Compose command:
```
docker-compose up
```

Once installed, you should be able to navigate to the site on port 8080. To get the IP for the site you can use `docker-machine ip <docker-machine-name>`.

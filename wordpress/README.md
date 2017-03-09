# Install WordPress Using Docker

<p align="center"><img src="https://s.w.org/about/images/logos/wordpress-logo-stacked-rgb.png" /></p>

> WordPress is an online, open source website creation tool written in PHP. But in non-geek speak, it's probably the easiest and most powerful blogging and website content management system (or CMS) in existence today.

For more information about this image, see [WordPress on Docker Hub](https://hub.docker.com/_/wordpress/).

This installation will also use the MariaDB Docker Image. For more on its image, see [MariaDB on Docker Hub](https://hub.docker.com/_/mariadb/).

### Use Docker Compose To Install WordPress
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

Navigate to that directory in your terminal and perform the following Docker Compose command:
```
docker-compose up
```

Once installed, you can navigate to the site on port 8080. To get the IP for the site you can use `docker-machine ip <docker-machine-name>`.

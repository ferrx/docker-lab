# Install Gitlab using Docker

<p align="center"><img src="https://cdn.xebialabs.com/assets/files/plugins/gitlab.jpg" /></p>

For more information about this image, see [Gitlab-ce on Dockerhub](https://hub.docker.com/r/gitlab/gitlab-ce/).

```
docker pull gitlab/gitlab-ce
```

```
docker run --detach \
    --hostname gitlab.example.com \
    --publish 443:443 --publish 80:80 --publish 22:22 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    gitlab/gitlab-ce:latest
```
To access your Gitlab-ce server, fetch the IP of your docker-machine with `docker-machine ip <docker-machine-name>` and browse to it. It may take a few minutes for Gitlab to spin up for the first time as it has many installations bootstrapped into it.

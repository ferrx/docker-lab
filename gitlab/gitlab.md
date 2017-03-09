# Install Gitlab using Docker

![Gitlab](https://forum.gitlab.com/uploads/default/original/1X/277d9badcbd723e913b3a41e64e8d2f3d2c80598.png)

For more information about this image, see [Gitlab-ce on Dockerhub](https://hub.docker.com/r/gitlab/gitlab-ce/).

`docker pull gitlab/gitlab-ce`

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

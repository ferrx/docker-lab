# Install Gitlab Using Docker

<p align="center"><img src="https://cdn.xebialabs.com/assets/files/plugins/gitlab.jpg" /></p>

> GitLab is an online Git repository manager with a wiki, issue tracking, CI and CD. It is a great way to manage git repositories on a centralized server. GitLab gives you complete control over your repositories or projects and allows you to decide whether they are public or private for free

For more information about this image, see [Gitlab-ce on Dockerhub](https://hub.docker.com/r/gitlab/gitlab-ce/).

```
docker pull gitlab/gitlab-ce
```

```
docker run --detach --hostname gitlab.example.com --publish 50443:443 --publish 50080:80 --publish 50022:22 --name gitlab --restart always --volume /srv/gitlab/config:/etc/gitlab --volume /srv/gitlab/logs:/var/log/gitlab --volume /srv/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce:latest
```
To access your Gitlab-ce server, fetch the IP of your docker-machine with `docker-machine ip <docker-machine-name>` and browse to it on port 50080 or at http://gitlab.example.com. It may take a few minutes for Gitlab to spin up for the first time as it has many installations bootstrapped into it.

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

## Gitlab Container's Run Commands Explained
For detailed documentation on all `run` commands, see docker's documentation [here](https://docs.docker.com/engine/reference/commandline/run/#options).
+ `--detach`: This command was used to run the container in the background
+ `--hostname`: This is the name for the host-facing IP address for the container
+ `--publish`: This is used to map a host port to a guest (container) port. Usage is `--publish <host-port>:<guest-port>`
+ `--restart`: This is the restart policy applied when the container exits. The options are `no`, `failure`, and `always`
+ `--volume`: This is a volume mapping on the host that the container can store data into. Usage is `--volume <host-file-path>:<guest-file-path>`. Normally, once a container is removed, all data will be lost. This is the ephemeral nature of a stateless container. However, when linking to a volume, you can remove and spin-up a container without losing the data, because the data will persist outside of the container.

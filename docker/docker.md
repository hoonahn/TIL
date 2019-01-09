# Docker

[Official Website](https://www.docker.com/)

[Official Documentation](https://docs.docker.com/)

> *"Docker provides a way to run applications securely isolated in a container, packaged with all its dependencies and libraries."*

## Remove all container and image

Sometimes we need to clean up remaining all containers.\
This is how to stop and remove all docker containers and images.

1. List all containers (only IDs).

```bash
$ docker ps -aq
e37211fe30a7
...
```

2. Stop all running containers.

```bash
$ docker stop $(docker ps -aq)
e37211fe30a7 # stoped.
...
```

3. Remove all containers.

```bash
$ docker rm $(docker ps -aq)
e37211fe30a7 # removed. check 'docker ps -a'
...
```

4. Remove all images.

```bash
$ docker rmi $(docker images -q)
# if neccessary
```

[Install Docker CE on Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-from-a-package)

[Docker Compose](./docker-compose.md)

#### Reference

- [Stop and remove all docker containers and images](http://blog.baudson.de/blog/stop-and-remove-all-docker-containers-and-images)

- [도커 이미지 만들고 배포하기](https://subicura.com/2017/02/10/docker-guide-for-beginners-create-image-and-deploy.html)
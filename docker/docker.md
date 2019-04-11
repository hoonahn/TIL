# Docker

[Official Website](https://www.docker.com/)

[Official Documentation](https://docs.docker.com/)

> *"Docker is a platform for developers and sysadmins to develop, deploy, and run applications with containers."*

## Concepts

[Orientation](https://docs.docker.com/get-started/)

**Containerization:** \
The use of Linux containers to deploy applications. \
리눅스 컨테이너를 사용하여 애플리케이션을 배포하는 것.

Features of containerization:
- Flexible: 복잡한 애플리케이션이라도 컨테이너화 가능
- Lightweight: 호스트의 커널을 공유하기 때문에 경량화됨
- Interchangeable: 애플리케이션 중단 없이 업데이트/업그레이드를 배포 가능
- Portable: 로컬에서 빌드하여 클라우드로 배포, 어디서든지 실행 가능
- Scalable: 컨테이너를 복제하여 규모를 증가 시키고 자동 분산시킬 수 있음
- Stackable: 연관된 서비스들을 하나의 스택으로 구성할 수 있음?

### Image and Container

**Image:** \
Executable package that includes everything needed to run an application; the code, a runtime, libraries, environment variables and configuration files. \
애플리케이션을 실행하는데 필요한 모든 것을 포함하는 실행 가능한 패키지; 코드, 런타임, 라이브러리, 환경 변수, 구성 파일 등.

**Container:** \
A runtime instance of an image; executed image in memory. (= an image with state or user process) \
이미지가 구동되고 있는 환경. 이미지가 실행되어 메모리에 올라간 상태. (= 상태가 있는 이미지)

### Docker Structure

Hierarchy of app in *Docker* way:
- Stack: 하나의 거대한 앱.
- Services: 앱을 구성하는 작은 앱들.
- Container: Service를 이루는 컨테이너. 

#### Containers
[link](https://docs.docker.com/get-started/part2/)

> “Docker builds images automatically by reading the instructions from a Dockerfile -- a text file that contains all commands, in order, needed to build a given image.”

- Defining a container w/ Dockerfile
  - [Dockerfile Refrence](https://docs.docker.com/engine/reference/builder/)
  - [Best Practice](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- Build/Run the app
- Share your image to Docker hub
  - [Docker Hub](https://hub.docker.com/)

#### Services
[link](https://docs.docker.com/get-started/part3/)

> Different pieces of the app in a distributed application. “Containers in production”. Runs only one image, codifying the way that image runs.

#### Stack
[link]()

---

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
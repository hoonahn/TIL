# Docker Compose

[Official Documentation](https://docs.docker.com/compose/)

> *"Compose is a tool for defining and running multi-container Docker applications."*

## Structure

Docker compose file is written in ```.yaml``` format.
Basic file name is ```docker-compose.yml``` and it will define the details of versions and options for the containers.

``` YAML
# This code block is just an example for decribing some options we can set on docker-compose.yml. The actual file may not run properly.

# Define version of Docker Compose.
version: "3"
# Define services we will use.
services:
  # Define name of the container. (It can be anything but simple name is recommanded.)
  db:
    image: postges # Without building, we can just bring the image.
    # Define directory where the volume data wil be stored.
    volumes: # Connect dir between local and container. Data will be preserved even the container is removed.
      - ./docker/data:/var/lib/postgresql/data # [local_dir:container_internal_dir]
    # Define enviroment variables. ex) USER, PASSWORD, AUTH, etc.
    environmnet:
      - POSTGRES_DB=sampledb
      - POSTGRES_USER=sampleuser
      - POSTGRES_PASSWORD=samplesecret
      - POSTGRES_INITDB_ARGS=--encoding=UTF-8
    # Healthcheck can check if its safe to run this container.
    healthcheck:
      # test command: 'pg_isready' checks whether database server is available to access.
      test: "pg_isready -h localhost -p 5432 -q -U postgres" 
      interval: 3s 
      timeout: 1s
      retries: 10
  web:
    # Set Build options.
    build: .
    # Define how to connect the ports. [Host port:Container port]
    ports:
      - "5000:5000"
    volumes:
      - .:/code
      - logvolume01:/var/log
    # Dependancy with other services. 
    depends_on:
      db:
        # With 'healthcheck' on 'db' and 'service_healthy', we can run web service after db service is healthy and ready.
        condition: service_healthy
    # In 'web' container, we can reference 'redis' or 'db'.
    links:
      - redis
      - db
    #some commands to run the docker run. It can be a actual command or a shell script.
    command:
      - command: /start_dev.sh
      # ex) /start_dev.sh
      # #!/bin/sh
      # python manage.py migrate
      # python manage.py runserver 0:5000
  redis:
    # Define name of the image and tag and also version(default is latest).
    image: redis
volumes:
  logvolume01: {}

```

1. ### When you edit the docker-compose.yml file.

If you just edited the docker-compose file and you want to see the difference, usually you have to stop the service(```stop```), remove it(```rm```) and restart it again(```up```).

But with the ```up``` command, it checks whether there is some difference and automatically re-creates the service and restart it.

```
$ docker-compose up -d [<name_of_the_service>]
```

If this doesn't work, use the ```--force-recreate``` option.

[Example of Django powered by docker compose](https://github.com/HoonAhn/dockercompose_django)

---

## YAML (***YAML Ain't Markup Language***)

> YAML is a human friendly data serialization standard for all programming languages.

### Primitives of YAML

- Scalar: String or number
- Sequence: Array or List
- Mapping: Hash or Dictionary. ```Key: Value``` type data structure
- Every blocks are seperated by indent, but YAML doesn't support tab(```\t```). Use 2 spaces for indent.
- Squence can be expressed by indent and ```-``` symbol
- Comment starts with ```#```
- Streams can be seperated by ```---``` and end with ```...```
- Repeating value can be set alias by ```&```

---

#### References

##### Docker

- [Docker (Compose) 활용법 - 개발 환경 구성하기](http://raccoonyy.github.io/docker-usages-for-dev-environment-setup/)

##### YAML

- [YAML 포맷이란](http://anitoy.pe.kr/yaml-format/)

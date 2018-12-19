# Docker Compose

[Official Documentation](https://docs.docker.com/compose/)

> *"Compose is a tool for defining and running multi-container Docker applications."*

## Structure

Docker compose file is written in ```.yaml``` format.
Basic file name is ```docker-compose.yml``` and it will define the details of versions and options for the containers.

``` YAML
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
    # Healthcheck
    healthcheck:
      test:
  web:
    # Set Build options.
    build: .
    # Define how to connect the ports. [Host port:Container port]
    ports:
    - "5000:5000"
    volumes:
    - .:/code
    - logvolume01:/var/log
    links:
    - redis
  redis:
    # Define name of the image and tag and also version(default is latest).
    image: redis
volumes:
  logvolume01: {}

```

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

##### YAML

- [YAML 포맷이란](http://anitoy.pe.kr/yaml-format/)

# Docker

## Docker Terminology
 - **image**: a snapshot of a container at a specific time, can be moved between systems
 - **container**: a running (or stopped) docker image

## Setup docker group
Run this to be able to run docker without root.

    $sudo usermod -a -G docker $USER    -- Create docker group and add yourself to it (to run docker without sudo)

## Run docker image
Create a container from an image and start the container
```bash
docker run [opt] image:[tag] [cmd] [arg...]`

 -d                            -- detatched (or deamon) background mode
 -p 8080:80                    -- Expose container port 80 to host port 8080
 -v /host:/container           -- Data on host path can be accessible from within container
 --name "elvis"                -- name your container
 --rm                          -- remove container after it stops
```

### Examples

    $docker run -it ubuntu bash          -- run bash from within the ubuntu docker with a -t terminal and -i interactive mode
    $docker run -d ubuntu my_script      -- run my_script as a -d deamon (in the background)

## Basic Commands
    docker stop <name|id>           -- Stop a running container
    docker start <name|id>          -- Start a container
    docker ps                       -- View all running containers
    docker ps -a                    -- View all containers (running and stopped)

## Useful commands
    docker ps -aq                   -- View all containers (running and stopped) in quiet mode (ID only)
    docker start -ai <name|id>      -- Start a stopped container, attach -a to it in interactive mode -i
    docker attach <name|id>         -- Attach to a running container
    docker rm <name|id>             -- Delete container
    docker rmi <name|id>            -- Delete image
    docker rm `docker ps -qa`       -- Delete all containers
    docker images                   -- List all images (-q quiet mode only shows IDs)
    docker logs                     -- Show the standard output of a container
    docker save -o f.tar <name|id>  -- Save docker image to f.tar (move to other host)
    docker load -i f.tar            -- Load docker image from f.tar
    docker pull alpine              -- Pull a the alpine image from docker HUB

## Docker restart
https://blog.codeship.com/ensuring-containers-are-always-running-with-dockers-restart-policy/

## Making an IMAGE from a DOCKERFILE
    $ mkdir dockerbuild
    $ cd dockerbuild
    $ vi Dockerfile
    > FROM docker/whalesay:latest                             -- starting image
    > RUN apt-get -y update && apt-get install -y fortunes    -- cmd to run during docker make
    > CMD /usr/games/fortune -a | cowsay                      -- cmd to run when docker starts
    
    $ docker build -t docker-whale .     -- Build from . and tag -t the docker as "docker-whale"
    $ docker images
    REPOSITORY   TAG     IMAGE ID       CREATED        VIRTUAL SIZE
    docker-whale latest  9ef91f8938ef   2 minutes ago  274.3 MB

## Making an IMAGE from a (stopped) container
    $ docker run -it ubuntu bash

    root@dockerID:/# sudo apt-get update
    root@dockerID:/# sudo apt-get install -y fortunes
    root@dockerID:/# /usr/games/fortune -n 1
    > "Whom are you?" said he, for he had been to night school.
    root@dockerID:/# exit

    $ docker ps -a
    CONTAINER ID   IMAGE           COMMAND   CREATED          STATUS
    b1f1fad64de8   ubuntu:latest   "bash"    4 minutes ago    Exited (0) 14 seconds ago
    
    $ docker commit -a "John Doe" b1f1fad64de8 jd/fortunes
    $ docker images
    REPOSITORY   TAG     IMAGE ID       CREATED        VIRTUAL SIZE
    jd/fortunes  latest  b5a589c8fe4a   8 seconds ago  215.4 MB
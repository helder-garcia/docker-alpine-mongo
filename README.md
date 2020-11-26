Mongo has changed their license so its package is not included anymore on main repository of Alpine Edge.
This image adds mongodb and mongodb-tools to the Alpine Edge. Mongo tools are important to have mainly due to mongodump and mongorestore utilities.
This repository is a modified fork of [mvertes/alpine-mongo](https://hub.docker.com/r/mvertes/alpine-mongo/)
This repository contains Dockerfile for [MongoDB 4.0.5](https://www.mongodb.org)
container, based on the [Alpine edge](https://hub.docker.com/_/alpine/) image.

As a prerequisite, you need [Docker](https://docker.com) to be installed.

## Install

To download this image from the public docker hub:

```
docker pull sounerd/alpine-mongo
```

To re-build this image from the dockerfile:

```
docker build -t sounerd/alpine-mongo .
```

## Usage

To run `mongod`:
```
docker run --detach --name mongo-test sounerd/alpine-mongo
```

You can also specify the database repository where to store the data with the volume -v option, and expose a TCP port with the -p option:

```
docker run --detach --name mongo-test -p 27017:27017 -v /somewhere/onmyhost/mydatabase:/data/db sounerd/alpine-mongo
```

To run a shell session:

```
docker exec -ti mongo-test /bin/ash
```

To use the mongo shell client:

```
docker exec -ti mongo-test mongo
```


## Build from source

If you want to build it from scratch, clone this repository locally and build the image, optionally tagging it:

```
docker build --tag my-image-name:1.0 .
```

Then create and start the container:

```
docker run --detach --name mongo-test my-image-name:1.0
```

## Limitations

- On MacOSX, volumes located in a virtualbox shared folder are not
  supported, due to a limitation of virtualbox (default docker-machine
  driver) not supporting fsync().

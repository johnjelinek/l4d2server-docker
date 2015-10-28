# Left 4 Dead 2 Server Dockerfile

This repository contains **Dockerfile** of [Left 4 Dead 2 Server](http://gameservermanagers.com/lgsm/l4d2server/) for [Docker](https://www.docker.com/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).

### Base Docker Image

* [ubuntu:14.04](https://hub.docker.com/_/ubuntu/)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/johnjelinek/l4dserver/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull johnjelinek/l4dserver`

   (alternatively, you can build an image from Dockerfile: `docker build -t="johnjelinek/l4dserver" github.com/johnjelinek/l4dserver-docker`)

### Usage

    docker run -dt --name l4d2 -v /var/docker/l4dserver:/home/l4dserver -p 27015:27015 \
    -p 27015:27015/udp --entrypoint /home/l4d2server/serverfiles/srcds_run johnjelinek/l4d2server \
    -game left4dead2 -strictportbind -ip 0.0.0.0 -port 27015 +clientport 27005 \
    +map c5m1_waterfront +servercfgfile l4d2-server.cfg -maxplayers 8

#### Preparation (Downloading the files onto your volume)

  1. Copy `/l4dserver` to `~/l4dserver`

  2. `./l4dserver install`

  3. Answer some questions

  4. You can test everything went well with `./l4dserver start` followed by `./l4dserver details`.

  5. If everything looks good, run with the command listed under `Usage`.

From Steam Menu, View > Servers > Add `yourServerIP` server as a favorite and double click to join.

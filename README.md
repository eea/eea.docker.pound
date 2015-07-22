## Pound load balancer Docker image

Docker images for Pound.

These images are generic, thus you can obviously re-use them within
your non-related EEA projects.


### Supported tags and respective Dockerfile links



### Base docker image

 - [hub.docker.com](https://registry.hub.docker.com/u/eeacms/pound)


### Source code

  - [github.com](http://github.com/eea/eea.docker.pound
)


### Installation

1. Install [Docker](https://www.docker.com/).



## Usage

    $ git clone https://github.com/eea/eea.docker.pound.git
    $ cd eea.docker.pound


### Run with Docker Compose
Using Docker Compose variable is the quickest way to start a container and connect the available webapps through the 'links' parameter. Here is a basic example of a `docker-compose.yml` file using the `eeacms/pound` docker image:

    webapp:
        image: razvan3895/nodeserver

    pound:
        image: eeacms/pound:latest
        links:
            - webapp
        ports:
            - "80:80"
        # env_file:
        #    - pound.env


The application can be scaled to use more server instances, with `docker-compose scale`:

    $ docker-compose scale webapp=<number of instances> pound=1


### Run with backends specified as environment variable

    $ docker run --env BACKENDS="172.17.1.83:80 172.17.1.84:80" eeacms/pound:latest

The servers are written as `server_ip:server_listening_port`, separated by spaces (and enclosed in quotes, to avoid issues). The contents of the variable are evaluated in a bash script that writes the Pound configuration file automatically.

### Use a custom configuration file mounted as a volume

    $ It is mandatory that the configuration file is mounted at /etc/pound/config.cfg
    $ docker run -v /absolute/path/to/pound/configuration:/etc/pound/config.cfg eeacms/pound:latest

This is the preferred way to start a container because the configuration file can be modified locally at any time. In order for the modifications to be applied, the configuration has to be reloaded, which can be done by running:

    $ docker exec <name-of-your-container> reload

## Supported environment variables ##

### pound.env ###

  As Pound has close to no purpose by itself, this image should be used in combination with others (for example with [Docker Compose](https://docs.docker.com/compose/)). Pound can be configured by modifying the following env variables, either when running the container or in a `docker-compose.yml` file, preferably by supplying an `.env` file in the appropriate tag.

  * `ALIVE` Specify how often Pound will check for resurected back-end hosts - `default` 30 seconds
  * `CLIENT` Specify for how long Pound will wait for a client request - `default` 10 seconds
  * `TIMEOUT` How long should Pound wait for a response from the back-end - `default` 15 seconds
  * `BACKENDS` The servers are written as `server_ip:server_listening_port`, separated by spaces (and enclosed in quotes, to avoid issues)


## Copyright and license

The Initial Owner of the Original Code is European Environment Agency (EEA).
All Rights Reserved.

The Original Code is free software;
you can redistribute it and/or modify it under the terms of the GNU
General Public License as published by the Free Software Foundation;
either version 2 of the License, or (at your option) any later
version.


## Funding

[European Environment Agency (EU)](http://eea.europa.eu)

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



### Usage

    $ git clone https://github.com/eea/eea.docker.pound.git
    $ cd eea.docker.pound

The docker image can be used by mounting a pound configuration file to /etc/pountd/config.cfg,
by setting the BACKENDS variable in pound.env file or by setting the links to applications in
docker-compose.

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

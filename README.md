# NSH Docker Test Network

This docker-compose project pulls repositories for an SF and a NSH traffic injector SFF, brings them up in a dedicated network, and sends traffic through them.  It can be used in conjunction with test scripts to run automated black box tests.

### Dependencies

These tests assume that docker and docker-compose are installed on the host system.  All other dependencies will be pulled in when the docker images are built, code is pulled and built, and docker network is run.  Docker images use ubuntu base images for SF and SFF builds and run time enviroment.


### Build

To build with the default repositories for SF and SFF run:

    docker-compose build

To change which repositories are used for either the SF or SFF simply change to the following lines in the sf or sff Dockerfile:

    RUN git clone https://github.com/<pointer to repository>

Private repositories can be used if the proper git userid and password are provided to grant permission.

### Run

First the docker images need to be build.

      docker-compose build --no-cache

Once the images are build, run:

     docker-compose up

This will run the conatiners in defualt mode.  If you wish to bring up the topology and log into the systems manually tweak the Dockerfile of each sf and sff to use the bash shell as the entry command and comment out the sf or sff start commands:

    #CMD ./nsh-sf-reflector
    CMD /bin/bash

Once this is done you can log into each container manually and start up the sf or sff for debugging:

    docker-compose up -d
    Jeffs-MBP-2:nsh-docker-network jeff$ docker exec -i -t sf-container bash



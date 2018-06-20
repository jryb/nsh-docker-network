# Start with ubuntu 16.04
FROM ubuntu:latest
MAINTAINER jeff.rybczynski@gmail.com

# For SSH access and port redirection
ENV ROOTPASSWORD lab123

# Update packages
RUN apt-get -y update

# Install system tools / libraries
RUN apt-get -y --fix-missing install make \
    gcc \
    libpthread-stubs0-dev \
    git

# Make sure the package repository is up to date
RUN mkdir -p /root/code
WORKDIR /root/code
RUN pwd

## Get SF code code
RUN git clone https://github.com/jryb/nsh-sf-reflector.git

## Build SF code
WORKDIR /root/code/nsh-sf-reflector/
RUN make

## Run SF code
#CMD ./nsh-sf-reflector

# For debugging, uncomment this following command to:
# - run a bash shell and start up reflector manually
CMD ["bash"]

# Start with ubuntu 16.04
FROM ubuntu:latest
MAINTAINER jeff.rybczynski@gmail.com

# For SSH access and port redirection
ENV ROOTPASSWORD lab123

# Update packages
RUN apt-get -y update

# Install system tools / libraries
RUN apt-get -y --fix-missing install gcc make libpcap-dev git

RUN mkdir -p /root/code
WORKDIR /root/code

## Get SFF/Traffic injector code code
RUN git clone https://github.com/jryb/nsh-traffic-injector.git

## Build SFF code
WORKDIR /root/code/nsh-traffic-injector/
RUN make

## Run SFF code using IP from docker-compose
#CMD ./nsh-traffic-injector -i 172.20.20.3 -p pcaps/test.pcap
CMD ["bash"]

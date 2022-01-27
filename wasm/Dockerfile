FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive
ARG VERSION=3.11.1
ARG ARCH=amd64

WORKDIR /root

RUN apt-get update -y
RUN apt-get install -y wget

# Install .Net 5
RUN wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN rm packages-microsoft-prod.deb
RUN apt-get update -y
RUN apt-get install -y apt-transport-https
RUN apt-get update -y
RUN apt-get install -y dotnet-sdk-5.0

# Install emscripten
RUN apt-get install -y git python3
RUN git clone https://github.com/emscripten-core/emsdk.git
WORKDIR /root/emsdk
RUN ./emsdk install latest
RUN ./emsdk activate latest
#RUN . ./emsdk_env.sh

ENV EMSDK=/root/emsdk \
    EM_CONFIG=/root/emsdk/.emscripten \
    EMSDK_NODE=/root/emsdk/node/14.18.2_64bit/bin/node \
    PATH="/root/emsdk:/root/emsdk/upstream/emscripten:/root/emsdk/upstream/bin:/root/emsdk/node/14.18.2_64bit/bin:${PATH}"

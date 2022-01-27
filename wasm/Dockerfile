FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive
ARG VERSION=3.11.1
ARG ARCH=amd64

WORKDIR /root

RUN apt-get update -y
RUN apt-get install -y wget

RUN wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN rm packages-microsoft-prod.deb
RUN apt-get update -y
RUN apt-get install apt-transport-https -y
RUN apt-get update -y
RUN apt-get install dotnet-sdk-5.0 -y

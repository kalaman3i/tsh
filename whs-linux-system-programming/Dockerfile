FROM ubuntu:22.04

RUN apt-get update \
 && apt-get install -y sudo

RUN adduser --disabled-password --gecos '' whitehat
RUN echo "whitehat:whitehat" | chpasswd
RUN adduser whitehat sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER whitehat
WORKDIR /home/whitehat
ARG DEBIAN_FRONTEND=noninteractive

RUN sudo sed -i 's/archive.ubuntu.com/ftp.daumkakao.com/g' /etc/apt/sources.list
RUN sudo sed -i 's/security.ubuntu.com/ftp.daumkakao.com/g' /etc/apt/sources.list
RUN sudo apt-get update && sudo apt-get upgrade -y
RUN sudo apt-get install build-essential gcc g++ vim git -y

COPY --chown=whitehat shlab-handout /home/whitehat/shlab-handout

CMD ["/usr/bin/bash"]

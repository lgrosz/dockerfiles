FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive 

# Essentials
RUN apt update && apt install -y gawk wget git diffstat unzip texinfo gcc \
build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils \
debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev \
pylint xterm python3-subunit mesa-common-dev zstd liblz4-tool

# Documentation
RUN apt update && apt install -y make python3-pip inkscape texlive-latex-extra
RUN pip3 install sphinx sphinx_rtd_theme pyyaml

# Missing packages
RUN apt update && apt install file

# Please make sure locale 'en_US.UTF-8' is available on your system 
RUN apt-get update && apt-get install -y locales
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen
ENV LC_ALL en_US.UTF-8 
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en

# `bitbake` cannot run as root
ENV HOME /home/chef
RUN useradd --create-home --home-dir $HOME chef
RUN chown -R chef:chef $HOME /run /tmp
USER chef
WORKDIR $HOME

ENTRYPOINT ["bash"]


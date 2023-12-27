FROM ubuntu:22.04

## Set timezone
ENV TZ=Asia/Tokyo
RUN echo TZ > /etc/timezone
RUN ln -snf /user/share/zoneinfo/$TZ /etc/localtime

## Install packages
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y \
    build-essential \
    libncursesw5-dev \
    libssl-dev \
    libsqlite3-dev \
    libgdbm-dev \
    libc6-dev \
    libbz2-dev \
    libffi-dev \
    tk-dev \
    zlib1g-dev \
    wget \
    locales \
    && apt clean \
    && rm -rf /var/lib/apt/lists/*

## Set locale
RUN locale-gen en_US.UTF-8
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8

# Install Python 3.11
RUN wget https://www.python.org/ftp/python/3.11.4/Python-3.11.4.tgz \
    && tar -zxf Python-3.11.4.tgz \
    && cd Python-3.11.4 \
    && ./configure --enable-optimizations \
    && make altinstall

# Set alias
RUN update-alternatives --install \
    /usr/local/bin/python3 python3 /usr/local/bin/python3.11 1
RUN update-alternatives --install \
    /usr/local/bin/pip3 pip3 /usr/local/bin/pip3.11 1

# Upgrade pip
RUN pip3 install -U pip

WORKDIR /root/mysite

ENV PYTHONUNBUFFERED=1

CMD ["/bin/bash"]
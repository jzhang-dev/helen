FROM pytorch/pytorch:1.13.0-cuda11.6-cudnn8-devel

# update and install dependencies
RUN apt-get update && \
    apt-get -y install git cmake make gcc g++ autoconf bzip2 lzma-dev zlib1g-dev && \
    apt-get -y install libcurl4-openssl-dev libpthread-stubs0-dev libbz2-dev liblzma-dev libhdf5-dev && \
    apt-get -y install python3-pip python3-virtualenv virtualenv && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN python3 -m pip uninstall -y numpy && \
    python3 -m pip install numpy==1.23.5

# get HELEN
WORKDIR /opt
RUN git clone https://github.com/jzhang-dev/helen.git && \
    cd /opt/helen && \
    git fetch && \
    git submodule update --init && \
    git pull origin master && \
    python3 -m pip install .

# setup entrypoint
WORKDIR /data



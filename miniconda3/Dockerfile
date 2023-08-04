# base image
FROM ubuntu:22.04

# set shell type
SHELL ["/bin/bash", "-c"]

# set path to conda
ENV PATH /opt/conda/bin:$PATH

# install packages
RUN apt-get update && apt-get install -y \
    wget \
    ca-certificates \
    bzip2 \
    && wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/miniconda.sh \
    && /bin/bash /tmp/miniconda.sh -b -p /opt/conda \
    && rm /tmp/miniconda.sh \
    && conda config --add channels r \
    && conda config --add channels defaults \
    && conda config --add channels conda-forge \
    && conda config --add channels bioconda \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*


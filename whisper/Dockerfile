# base image
FROM ubuntu:22.04

# set shell type
SHELL ["/bin/bash", "-c"]

# install packages
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    git \
    wget

# install whisper from github
RUN git clone https://github.com/ggerganov/whisper.cpp.git /whisper
WORKDIR /whisper
RUN bash models/download-ggml-model.sh large && \
    make

# make directory for workspace
RUN mkdir /app
WORKDIR /app

# bash
CMD ["../bin/bash"]
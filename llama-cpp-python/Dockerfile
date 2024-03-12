# base image
ARG CUDA_IMAGE="12.3.2-cudnn9-devel-ubuntu22.04"
FROM nvidia/cuda:${CUDA_IMAGE}

# set shell type
SHELL ["bin/bash", "-c"]

# set environmental variables
ENV LLAMA_CUBLAS=1
ENV FORCE_CMAKE=1
ENV CMAKE_ARGS="-DLLAMA_CUBLAS=on"

# install packages
RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y wget python3 python3-pip cmake \
    && pip3 install llama-cpp-python

# chnage directory
WORKDIR /tmp

# bash
CMD ["../bin/bash"]

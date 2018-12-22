FROM opensuse:42.2

LABEL maintainer "503045944@ge.com"

ENV SUSE_OS opensuse422

ENV CUDA_VERSION 9.0.176

ENV CUDA_PKG_VERSION 9-0-${CUDA_VERSION}-1

ENV CUDA_REPO http://developer.download.nvidia.com/compute/cuda/repos/${SUSE_OS}/x86_64/

#ADD cudnn-9.0-linux-x64-v7.3.1.20.tgz /usr/local/cuda

RUN zypper -n ar http://developer.download.nvidia.com/compute/cuda/repos/${SUSE_OS}/x86_64/ cuda && \
    zypper --gpg-auto-import-keys install -y \
              cuda-cudart-$CUDA_PKG_VERSION  \
              cuda-libraries-$CUDA_PKG_VERSION \
              cuda-cublas-9-0-9.0.176.4-1      &&\
    ln -s cuda-9.0 /usr/local/cuda && \
     rm -rf /var/cache/zypp/* 

ENV PATH /usr/local/nvidia/bin:/usr/local/cuda/bin:${PATH}

ENV LD_LIBRARY_PATH /usr/local/nvidia/lib:/usr/local/nvidia/lib64:/usr/local/cuda/lib64:${LD_LIBRARY_PATH}

ENV NVIDIA_DRIVER_CAPABILITIES compute,utility

ENV NVIDIA_REQUIRE_CUDA "cuda>=9.0"

WORKDIR /usr/g/ctuser



FROM library/ubuntu:16.04

LABEL maintainer="Chris Diehl <cultclassik@gmail.com>"

#ENV AMD_DRIVER="https://s3-us-west-1.amazonaws.com/mastermine/minebox/amdgpu-pro-17.50-511655.tar.xz"
ENV AMD_DRIVER="https://diehlabstorage.blob.core.windows.net/mine/amdgpu-pro-19.20-812932-ubuntu-18.04.tar.xz"
#ENV MINER_URL="https://s3-us-west-1.amazonaws.com/mastermine/minebox/claymore_eth_11.7_linux.tar.gz"
ENV MINER_URL="https://diehlabstorage.blob.core.windows.net/mine/Claymore's%20Dual%20Ethereum%20AMD+NVIDIA%20GPU%20Miner%20v14.7%20-%20LINUX.tar.gz"
WORKDIR /tmp

RUN apt-get update && apt-get install -y \
    libcurl3 \
    wget \
    xz-utils \
 && wget ${AMD_DRIVER} \
 && unxz amdgpu-pro-19.20-812932-ubuntu-18.04.tar.xz \
 && tar -xvf *.tar \
 && rm *.tar \
 && ./amdgpu-pro-19.20-812932-ubuntu-18.04/amdgpu-pro-install --opencl=legacy,rocm --headless -y \
 && rm -rf ./*

RUN mkdir /claymore \
 && wget ${MINER_URL} \
 && tar -xvf ./*.tar.gz -C /claymore --strip-components 1 \
 && rm ./*.tar.gz \
 && rm -rf /var/lib/apt/lists/* \
 && chmod +x /claymore/ethdcrminer64

WORKDIR /claymore

EXPOSE 3333/tcp

ENTRYPOINT [ "/claymore/ethdcrminer64" ]
CMD [ "-epool", "mypool.org", "-ewal", "0xfdf87w987fw98" ]
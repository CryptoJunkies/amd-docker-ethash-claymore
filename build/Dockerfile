FROM library/ubuntu:16.04

LABEL maintainer="Chris Diehl <cultclassik@gmail.com>"

ENV AMD_DRIVER="https://s3-us-west-1.amazonaws.com/mastermine/minebox/amdgpu-pro-18.10-572953.tar.xz"
ENV MINER_URL="https://s3-us-west-1.amazonaws.com/mastermine/minebox/claymore_eth_11.7_linux.tar.gz"

WORKDIR /tmp

RUN apt-get update && apt-get install -y \
    libcurl3 \
    wget \
    xz-utils \
 && wget ${AMD_DRIVER} \
 && unxz amdgpu-pro-18.10-572953.tar.xz \
 && tar -xvf *.tar \
 && rm *.tar \
 && ./amdgpu-pro-18.10-572953/amdgpu-pro-install --opencl=legacy,rocm --headless -y \
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
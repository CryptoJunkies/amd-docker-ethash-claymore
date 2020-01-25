FROM library/ubuntu:18.04

LABEL maintainer="Chris Diehl <cultclassik@gmail.com>"

ENV AMD_DRIVER="https://storageroot.blob.core.windows.net/mining/amdgpu-pro-19.50-967956-ubuntu-18.04.tar.xz?sp=r&st=2020-01-25T03:32:23Z&se=2021-01-01T11:32:23Z&spr=https&sv=2019-02-02&sr=b&sig=r38KLzAeqIOVZGDCNhPv4jdexpp%2B%2BY%2Bcm1sdMAsLQLk%3D"
ENV DRIVER_FILE="amdgpu-pro-19.50-967956-ubuntu-18.04"
ENV MINER_URL="https://storageroot.blob.core.windows.net/mining/Claymore's%20Dual%20Ethereum%20AMD%2BNVIDIA%20GPU%20Miner%20v15.0%20-%20LINUX.tar.gz?sp=r&st=2020-01-25T03:31:19Z&se=2021-01-01T11:31:19Z&spr=https&sv=2019-02-02&sr=b&sig=mErrtmTFpFFOrQK%2B2qNCYCt%2BYaIYrrReYuOjqBTsUn4%3D"

WORKDIR /tmp

RUN apt-get update && apt-get install -y \
    libcurl3 \
    wget \
    xz-utils \
 && wget ${AMD_DRIVER} -O ./${DRIVER_FILE}.tar.xz\
 && unxz  \
 && tar -xvf *.tar \
 && rm *.tar \
 && ./${DRIVER_FILE}/amdgpu-pro-install --opencl=legacy,rocm --headless -y \
 && rm -rf ./*

RUN mkdir /claymore \
 && wget ${MINER_URL} -O ./claymore.tar.gz \
 && tar -xvf ./claymore.tar.gz -C /claymore --strip-components 1 \
 && rm ./*.tar.gz \
 && rm -rf /var/lib/apt/lists/* \
 && chmod +x /claymore/ethdcrminer64

WORKDIR /claymore

EXPOSE 3333/tcp

ENTRYPOINT [ "/claymore/ethdcrminer64" ]
CMD [ "-epool", "mypool.org", "-ewal", "0xfdf87w987fw98" ]
# amd-docker-ethash-claymore [![Build Status](https://travis-ci.org/CultClassik/amd-docker-ethash-claymore.svg?branch=master)](https://travis-ci.org/CultClassik/amd-docker-ethash-claymore)
[Image on Docker Hub](https://hub.docker.com/r/cryptojunkies/claymore/)

Dockerfile to build cryptojunkies/claymore GPU mining container.

Incorporates Claymore's dual ETH miner.

## Pre-requisites

Requires a working installation of Docker CE or EE and Nvidia-Docker2.

## Installation

docker build -t cultclassik/claymore-eth:eth-amd-latest ./build

## Usage

docker run --device=/dev/dri cryptojunkies/claymore:eth-amd-latest "-epool mypool.org -ewall myethaccount etc"

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

2018-27-05
Updated AMD drivers from 17.50 to 18.10
Updated Claymore from 11.0 to 11.7

2018-13-01
Initial creation and build by CultClassik

## Credits

TODO: Write credits

## License

TODO: Write license
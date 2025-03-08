# fgms-docker

This repository provides Docker images for the FlightGear Multiplayer Server (FGMS) across various platforms and distributions.

## About
FGMS is the multiplayer server component of [FlightGear](https://www.flightgear.org/), an open-source flight simulator. This repository automates the process of building and packaging FGMS into Docker containers, making it easy to deploy and run on different environments.

## Features
- Prebuilt Docker images for FGMS
- Support for multiple Linux distributions
- Configurable environment variables for server settings
- Lightweight and efficient setup for hosting FlightGear multiplayer sessions

## Supported platforms and distributions and tags
- ghcr.io/t3r/fgms:alpine-latest
- ghcr.io/t3r/fgms:debian-latest
- ghcr.io/t3r/fgms:ubuntu-latest

Uncertain which one to use? Pick the alpine based image which is by far the smallest one (just over 11MB). Debian and ubuntu images are both around 100MB, doing the same thing.

The images run on x86_64 (a.k.a amd64), arm64 and arm/v7 platforms so you should be able to run it on most Intel/AMD computers as well as on raspberry pi with 32bit and 64bit operating system.

## Getting Started

### Prerequisites
- Docker installed on your system

### Running FGMS with Docker
To start a basic FGMS container, use the following command:
```sh
docker run -d --name fgms -p 5000:5000/udp \
                          -p 5001:5001/tcp \
                          -v /path/to/your/fgms.conf:/usr/local/etc/fgms.conf:ro \
                          ghcr.io/t3r/fgms:alpine-latest
```
This will run the server in detached mode and expose the default FGMS port (5000) as well as the default telnet port (5001). Please
note that the image does not provide a config file. You need to mount a local and customized copy into the container.

## Building the Image
To build the Docker image locally, clone the repository and run:
```sh
git clone https://github.com/t3r/fgms-docker.git
cd fgms-docker
docker build -t fgms -f Dockerfile.alpine .
```

## Contributing
Contributions are welcome! Feel free to open issues or submit pull requests to improve the repository.

## License
This project is licensed under the terms of the [GPLv2+](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html), in line with FlightGear's licensing.

## Acknowledgments
- [FlightGear](https://www.flightgear.org/)
- The FlightGear Multiplayer Server (FGMS) community


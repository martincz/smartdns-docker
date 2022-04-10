# SmartDNS - Docker

## Introduction
SmartDNS is a local DNS server. SmartDNS accepts DNS query requests from local clients, obtains DNS query results from multiple upstream DNS servers, and returns the fastest access results to clients. Avoiding DNS pollution and improving network access speed, supports high-performance ad filtering.

Unlike dnsmasq's all-servers, smartdns returns the fastest access resolution. 

## Quick Start

**Pull the Docker image**

This command will pull the latest stable version:

    docker pull chihpengkao/smartdns

**Create directories for persistent configuration**

The image exposes a volume for configuration persistence. You should create a **configuration** directory on a suitable volume on your host system, e.g. `/opt/docker/smartdns`.

**Create and run the container**

Use the following command to create a new container and run SmartDNS:

    docker run --name smartdns\
        --restart unless-stopped\
        -v /opt/docker/smartdns:/etc/smartdns
        -p 1053:53/tcp -p 1053:53/udp\
        -d chihpengkao/smartdns

Ports mappings you may need:

* `-p 53:53/tcp -p 53:53/udp` : plain DNS.

**Control the container**

* Start: `docker start smartdns`

* Stop: `docker stop smartdns`

* Remove: `docker rm smartdns`

## Update To A Newer Version

1.  Pull the new version from Docker Hub:

        docker pull chihpengkao/smartdns

2. Stop and remove currently running container (assuming the container is named smartdns):

        docker stop smartdns
        docker rm smartdns

3. Create and start the container using the new image using the command from the previous section.
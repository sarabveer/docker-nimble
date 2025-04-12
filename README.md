# Nimble Streamer 3.7.13-3 Docker Image

This container provides [nimble](https://softvelum.com/nimble/) v3.7.13-3 as a Docker container. This container is only for the amd64 platform as the available binary is compiled for amd64.

Nimble Streamer v3.7.13-3 is the last "freemium" version of Nimble, however the packages for this version have been removed from Softvelum repos. This container image was created for anyone still wanting to run this version of Nimble.

## Usage

From Docker registry:

```
docker pull ghcr.io/sarabveer/docker-nimble:latest
```

Or build yourself:

```
git clone https://github.com/sarabveer/docker-nimble.git
docker build -t ghcr.io/sarabveer/docker-nimble --platform=linux/amd64 .
```

Running the image:

```
docker run --rm -p 8081:80 -v ~/nimble:/etc/nimble --name nimble ghcr.io/sarabveer/docker-nimble
```

## Configuration

The configuration is stored under `/etc/nimble/`, with two files `nimble.conf` and `rules.conf`.

It is assumed that one would have a copy of these files from their current running instance.

The standard way to configure Nimble is through WMSPanel. While documentation for `nimble.conf` is provided by Softvelum [here](https://softvelum.com/nimble/param/) [^1]. A sample `nimble.conf` is provided [here](https://github.com/sarabveer/docker-nimble/blob/main/rootfs/etc/nimble/nimble.conf).

[^1]:  Note that this documentation is for Nimble 4.x and may have differing config options.

However, providing a sample `rules.conf` is not possible as this was only configured through WMSPanel. This file is a JSON file containing configuration for the media streams, ingest interfaces, etc. Once this file was configured, it could be modified offline without syncing to WMSPanel.

### Volume

Mount the `/etc/nimble/` folder to a volume or bind mount, as the container does not ship with a default config aside from the sample `nimble.conf` file.

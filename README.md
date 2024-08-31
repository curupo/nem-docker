# NIS Docker

Customized Docker files provided by the [core team](https://github.com/NemProject/nem-docker).
Customized Docker files provided by the [Yoshiyuki IEYAMA](https://github.com/44uk/nem-docker).

To participate in the [Supernode Program](https://docs.nem.io/pages/Guides/supernode-program/docs.en.html), please see below.


## Prerequisites

[Docker](https://docs.docker.com/get-docker/) installation is required.

## Installation

Clone [this repository](https://github.com/curupo/nem-docker):

```bash
$ git clone https://github.com/curupo/nem-docker.git
$ cd nem-docker
```

## How to run

The required values must be set. See the [documentation](https://docs.nem.io/pages/) for details:


```text
$ vi .docker/nis/config-user.properties
```

If you are participating in the Supernode Program, you will also need the following:

```text
$ vi .docker/servant/config.properties
```

Build and start the docker container:

```bash
$ docker-compose up -d
```

```bash
$ curl http://localhost:7890/node/extended-info
$ curl http://localhost:7890/chain/height
```

# Docker Curator

## Background

One of the best things about Docker is the ability to create build scripts that allow anyone to re-create a working environment.

In order to achieve this it is important to specify version numbers in your docker files as demonstrated in the Dockerfile of my python-lev project:

```
ARG PYTHON_VERSION=3.9
ARG ALPINE_VERSION=3.13

FROM python:${PYTHON_VERSION}-alpine${ALPINE_VERSION} AS builder

RUN apk add --no-cache g++

RUN pip install --user --no-cache-dir python-Levenshtein==0.12.*

FROM python:${PYTHON_VERSION}-alpine${ALPINE_VERSION}

COPY --from=builder /root/.local/lib/ /usr/local/lib/
```

Points of note in this example:

- The parent Docker image is python:3.9-alpine3.13
  - Python is essentially pinned at version 3.9.* - e.g. 3.9.2
  - Alpine is essentially pinned at version 3.13.* - e.g. 3.13.2
- The library python-Levenshtein is pinned at version 0.12.* - e.g. 0.12.2

Since Python, Alpine and PIP use [semantic versioning](https://semver.org/), I allow use the latest patch release but not the latest major or minor releases. This allows me to chose when I move to the next major or minor release but only after reviewing the release notes.

The biggest advantage is that the Dockerfile can be shared and re-used with high confidence of a consistent Docker image. The downside to this approach is that it necessitates the need for periodic updates to the Dockerfile.



## Docker Curator

### Docker Images

The way that I monitor for new Docker images is via a homemade Python script which I have called the Docker Curator.

The script uses a simple JSON configuration file and searches Docker Hub for newer versions of specific images.

Once I know what new Docker images are available, I go through my projects and update them accordingly:

- Firstly, I update my public repositories on Docker Hub - see further [details](dockerhub/README.md)
- Secondly, I update my public and private repositories on GitHub - see further [details](github.md)





## Additional Dependencies

### Python

#### PIP

Many of my projects and Docker images install images from PyPI using "pip".

I have listed these libraries in a separate [pip](pip/README.md) document.



### System Packages

#### Alpine

Alpine system packages are installed using "apk".

I have listed the Alpine packages in a separate [alpine](alpine.md) document.



#### Debian (slim)

Debian packages are installed using "apt-get".

I have listed the Debian  packages in a separate [Debian (slim)](debian-slim.md) document.

  

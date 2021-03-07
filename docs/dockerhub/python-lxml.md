## Docker Hub

### logiqx/python-lxml

This image has been created primarily as a parent image for logiqx/python-bs4.

Aside from Python it includes [lxml](https://pypi.org/project/lxml/#history) which sees a new minor release (e.g. version 4.6.0) approximately twice a year.



### Update Process

1. Edit Dockerfile(s) + README.
2. Create some temporary environment variables, ensuring that the appropriate Docker images have already been [pulled](README.md).

```
IMAGE=python-lxml

PYTHON_VERSION=3.9
ALPINE_VERSION=3.13
DEBIAN_VERSION=buster

LXML_VERSION=4.6
```

3. Build and test the images locally

```
docker image build . -t ${IMAGE}:${PYTHON_VERSION}-alpine${ALPINE_VERSION}
docker image build . -f Dockerfile-slim -t ${IMAGE}:${PYTHON_VERSION}-slim-${DEBIAN_VERSION}
```

5. Apply updates to git.

```
git add Dockerfile* README.md
git commit -m "Update to Python ${PYTHON_VERSION}, Alpine ${ALPINE_VERSION}, lxml ${LXML_VERSION}"
git push

for TAG in ${PYTHON_VERSION}-alpine${ALPINE_VERSION} ${PYTHON_VERSION}-slim-${DEBIAN_VERSION}
do
    git tag ${TAG}
    git push origin ${TAG}
done
```

6. Wait for automated builds then run on Docker Hub.
7. Create alternative tag(s) for Alpine images:

```
docker pull logiqx/${IMAGE}:${PYTHON_VERSION}-alpine${ALPINE_VERSION}

for TAG in ${PYTHON_VERSION}-alpine latest
do
    docker tag logiqx/${IMAGE}:${PYTHON_VERSION}-alpine${ALPINE_VERSION} logiqx/${IMAGE}:${TAG}
    docker push logiqx/${IMAGE}:${TAG}
done
```

8. Create alternative tag(s) for Debian images:

```
docker pull logiqx/${IMAGE}:${PYTHON_VERSION}-slim-${DEBIAN_VERSION}

for TAG in ${PYTHON_VERSION}-slim
do
    docker tag logiqx/${IMAGE}:${PYTHON_VERSION}-slim-${DEBIAN_VERSION} logiqx/${IMAGE}:${TAG}
    docker push logiqx/${IMAGE}:${TAG}
done
```


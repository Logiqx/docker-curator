## Docker Hub

### logiqx/python-lev

This image has been created primarily for an online cubing [competition](https://logiqx.github.io/scw-comp/).

Aside from Python it includes [python-Levenshtein](https://pypi.org/project/python-Levenshtein/#history) which rarely sees a new minor release (e.g. version 0.12.0).



### Update Process

1. Edit Dockerfile(s) + README.
2. Create some temporary environment variables, ensuring that the appropriate Docker images have already been [pulled](README.md).

```
IMAGE=python-lev

PYTHON_VERSION=3.9
ALPINE_VERSION=3.13
DEBIAN_VERSION=buster

LEV_VERSION=0.12
```

3. Build and test the images locally

```
docker image build . -t ${IMAGE}:${PYTHON_VERSION}-alpine${ALPINE_VERSION}
docker image build . -f Dockerfile-slim -t ${IMAGE}:${PYTHON_VERSION}-slim-${DEBIAN_VERSION}
```

5. Apply updates to git.

```
git add Dockerfile* README.md
git commit -m "Update to Python ${PYTHON_VERSION}, Alpine ${ALPINE_VERSION}, python-Levenshtein ${LEV_VERSION}"
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


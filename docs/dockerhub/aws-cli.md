## Docker Hub

### logiqx/aws-cli

This image has been created primarily for an online cubing [competition](https://logiqx.github.io/scw-comp/).

Aside from Python it includes [aws-cli](https://pypi.org/project/awscli/#history) which sees a new minor release (e.g. version 0.12.0) approximately once a year.



### Update Process

1. Edit Dockerfile(s) + README.
2. Create some temporary environment variables, ensuring that the appropriate Docker images have already been [pulled](README.md).

```
IMAGE=aws-cli

PYTHON_VERSION=3.9
ALPINE_VERSION=3.13
DEBIAN_VERSION=buster

AWS_VERSION=1.19
```

3. Build and test the images locally

```
docker image build . -t ${IMAGE}:${AWS_VERSION}-alpine${ALPINE_VERSION}
docker image build . -f Dockerfile-slim -t ${IMAGE}:${AWS_VERSION}-slim-${DEBIAN_VERSION}
```

5. Apply updates to git.

```
git add Dockerfile* README.md
git commit -m "Update to Python ${PYTHON_VERSION}, Alpine ${ALPINE_VERSION}, awscli ${AWS_VERSION}"
git push

for TAG in ${AWS_VERSION}-alpine${ALPINE_VERSION} ${AWS_VERSION}-slim-${DEBIAN_VERSION}
do
    git tag ${TAG}
    git push origin ${TAG}
done
```

6. Wait for automated builds then run on Docker Hub.
7. Create alternative tag(s) for Alpine images:

```
docker pull logiqx/${IMAGE}:${AWS_VERSION}-alpine${ALPINE_VERSION}

for TAG in ${AWS_VERSION}-alpine latest
do
    docker tag logiqx/${IMAGE}:${AWS_VERSION}-alpine${ALPINE_VERSION} logiqx/${IMAGE}:${TAG}
    docker push logiqx/${IMAGE}:${TAG}
done
```

8. Create alternative tag(s) for Debian images:

```
docker pull logiqx/${IMAGE}:${AWS_VERSION}-slim-${DEBIAN_VERSION}

for TAG in ${AWS_VERSION}-slim
do
    docker tag logiqx/${IMAGE}:${AWS_VERSION}-slim-${DEBIAN_VERSION} logiqx/${IMAGE}:${TAG}
    docker push logiqx/${IMAGE}:${TAG}
done
```


## Docker Hub

### logiqx/mysql-client

This image has been created primarily for quick database checks from my Jenkins jobs.

It only includes the MySQL / MariaDB client which sees a new minor release (e.g. version 0.12.0) approximately once a year. TBC



### Update Process

1. Edit Dockerfile(s) + README.
2. Create some temporary environment variables, ensuring that the appropriate Docker images have already been [pulled](README.md).

```
IMAGE=mysql-client

ALPINE_VERSION=3.13
DEBIAN_VERSION=buster

ALPINE_MARIADB_VERSION=10.5
DEBIAN_MARIADB_VERSION=10.3
```

3. Build and test the images locally

```
docker image build . -t ${IMAGE}:${ALPINE_MARIADB_VERSION}-alpine${ALPINE_VERSION}
docker image build . -f Dockerfile-slim -t ${IMAGE}:${DEBIAN_MARIADB_VERSION}-slim-${DEBIAN_VERSION}
```

5. Apply updates to git.

```
git add Dockerfile* README.md
git commit -m "Update to Alpine ${ALPINE_VERSION}, awscli ${AWS_VERSION}"
git push

for TAG in ${ALPINE_MARIADB_VERSION}-alpine${ALPINE_VERSION} ${DEBIAN_MARIADB_VERSION}-slim-${DEBIAN_VERSION}
do
    git tag ${TAG}
    git push origin ${TAG}
done
```

6. Wait for automated builds then run on Docker Hub.
7. Create alternative tag(s) for Alpine images:

```
docker pull logiqx/${IMAGE}:${ALPINE_MARIADB_VERSION}-alpine${ALPINE_VERSION}

for TAG in ${ALPINE_MARIADB_VERSION}-alpine latest
do
    docker tag logiqx/${IMAGE}:${ALPINE_MARIADB_VERSION}-alpine${ALPINE_VERSION} logiqx/${IMAGE}:${TAG}
    docker push logiqx/${IMAGE}:${TAG}
done
```

8. Create alternative tag(s) for Debian images:

```
docker pull logiqx/${IMAGE}:${DEBIAN_MARIADB_VERSION}-slim-${DEBIAN_VERSION}

for TAG in ${DEBIAN_MARIADB_VERSION}-slim
do
    docker tag logiqx/${IMAGE}:${DEBIAN_MARIADB_VERSION}-slim-${DEBIAN_VERSION} logiqx/${IMAGE}:${TAG}
    docker push logiqx/${IMAGE}:${TAG}
done
```


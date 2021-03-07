## Docker Hub

### Public Repositories on Docker Hub

I have a number of lightweight Docker images on Docker Hub, generally built for convenience on AWS:

- [logiqx/aws-cli](aws-cli.md)
- [logiqx/mysql-client](mysql-client.md)
- [logiqx/python-lev](python-lev.md)
- [logiqx/python-lxml](python-lxml.md)
  - [logiqx/python-bs4](python-bs4.md)

Note: I've deliberately indented python-bs4 because python-lxml is the parent image.



### General Process

#### Pull Latest Images

1. Start by setting some temporary environment variables:

```
PYTHON_VERSION=3.9
ALPINE_VERSION=3.13
DEBIAN_VERSION=buster
```

2. Pull the required Docker images:

```
docker pull alpine:${ALPINE_VERSION}
docker pull debian-slim:${DEBIAN_VERSION}

docker pull python:${PYTHON_VERSION}-alpine${ALPINE_VERSION}
docker pull python:${PYTHON_VERSION}-slim-${DEBIAN_VERSION}
```



#### Generic Builds

I have a generic process for updating each of my repositories on Docker Hub; building and tagging Docker images.

1. Edit the Dockerfile(s) + README.

```
git add Dockerfile* README.md
git commit -m "Update ..."
git push

git tag [tagname]
git push origin [tagname]
```

2. Wait for automated build to run on Docker Hub.
3. Retrieve the new images, create additional tags and push the tags back to Docker Hub.

```
docker pull [image]
docker tag [image:tagname] [image:alt_tagname_1]
docker tag [image:tagname] [image:alt_tagname_2]
...
docker push [image:alt_tagname_1]
docker push [image:alt_tagname_2]
...
```

Separate documents exist for each image and can be viewed by clicking the links at the top of this document.



## Alpine

### System Packages

Alpine packages are installed using "apk".

Package versions for Alpine can be determined via the package [filter / search](https://pkgs.alpinelinux.org/packages) at [pkgs.alpinelinux.org](https://alpinelinux.org/).

Note: I only specify version numbers for a few of the Alpine system packages; e.g. tini and mysql-client.



#### tini

tini ~0.19 is used as the ENTRYPOINT of projects based on Alpine 3.12 and newer.



#### mysql-client

mysql-client ~10.5 is used by all projects based on Alpine 3.13 and newer.

- logiqx/mysql-client

- wca-db



#### libxml + libxslt

libxml2 ~2.9 and libxslt ~1.1 are used by one project:

- logiqx/python-lxml

libxml2-dev ~2.9 and libxslt-dev ~1.1 are used during the multi-stage build of one project:

- logiqx/python-lxml



#### g++

g++ is used during multi-stage builds:

- logiqx/python-lxml
- logiqx/python-lev



#### docker

docker is used by one project:

- wca-compose (jenkins)



#### groff

groff is only used by one project:

- logiqx/aws-cli




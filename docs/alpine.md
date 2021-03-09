## Alpine

### System Packages

Alpine packages are installed using "apk".

I only specify version numbers for  handful of system packages such as tini and the mysql-client.



#### tini

tini ~0.18 and ~0.19 are used as the Docker ENTRYPOINT in many of my projects.



#### mysql-client

mysql-client ~is used by a few projects:

~10.5

- logiqx/mysql-client

~10.4 

- wca-db



#### libxml + libxslt

libxml2 and libxslt1.1 are used by one project:

- logiqx/python-lxml

libxml2-dev and libxslt-dev are used during the multi-stage build of one project:

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


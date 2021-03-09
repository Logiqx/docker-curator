## Debian (slim)

### System Packages

Debian packages are installed using "apt-get".

I only specify version numbers for  handful of system packages such as tini and the mariadb-client.



#### tini

tini 0.18.\* is used as the Docker ENTRYPOINT in many of my projects.



#### mariadb-client

mariadb-client-10.3 is used by a few projects:

- logiqx/mysql-client
- wca-db



#### libxml + libxslt

libxml2 and libxslt1.1 are used by one project:

- logiqx/python-lxml



#### gcc

gcc is used during multi-stage builds:

- logiqx/python-lev



#### imagemagick

imagemagick is used by one project:

- visualcube



#### groff

groff is only used by one project:

- logiqx/aws-cli


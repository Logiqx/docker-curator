## Operating Systems

### Alpine Linux
### alpine:3.10 - NEEDS ATTENTION

Docker Hub - https://hub.docker.com/_/alpine
News - https://alpinelinux.org/posts/
Releases - https://alpinelinux.org/releases/

    3
      latest = 3

    3.11
      3 != 3.11
        ['latest', '3.13.2', '3.13', '3']



### Debian
### debian:buster

Docker Hub - https://hub.docker.com/_/debian
News - https://www.debian.org/News/
Releases - https://wiki.debian.org/DebianReleases

    Buster
      latest = buster



### Ubuntu
### ubuntu:bionic - NEEDS ATTENTION

Docker Hub - https://hub.docker.com/_/ubuntu
News - https://lists.ubuntu.com/
Releases - https://wiki.ubuntu.com/Releases

    Bionic
      latest != bionic
        ['latest', 'focal-20210217', 'focal', '20.04']



## Programming Languages

### Python
### python:3.8-alpine3.11 - NEEDS ATTENTION

Docker Hub - https://hub.docker.com/_/python
News - https://www.python.org/blogs/
Releases - https://www.python.org/downloads/

    3
      latest = 3

    3.8
      3 != 3.8
        ['latest', 'buster', '3.9.2-buster', '3.9.2', '3.9-buster', '3.9', '3-buster', '3']

    3.8 Slim
      slim = 3-slim
      3-slim != 3.8-slim
        ['slim-buster', 'slim', '3.9.2-slim-buster', '3.9.2-slim', '3.9-slim-buster', '3.9-slim', '3-slim-buster', '3-slim']

    3.8 Slim Buster
      slim = slim-buster
      slim-buster = 3-slim-buster
      3-slim-buster != 3.8-slim-buster
        ['slim-buster', 'slim', '3.9.2-slim-buster', '3.9.2-slim', '3.9-slim-buster', '3.9-slim', '3-slim-buster', '3-slim']

    3.8 Alpine
      alpine = 3-alpine
      3-alpine != 3.8-alpine
        ['alpine3.13', 'alpine', '3.9.2-alpine3.13', '3.9.2-alpine', '3.9-alpine3.13', '3.9-alpine', '3-alpine3.13', '3-alpine']

    3.8 Alpine 3.11
      alpine != alpine3.11
        ['alpine3.13', 'alpine', '3.9.2-alpine3.13', '3.9.2-alpine', '3.9-alpine3.13', '3.9-alpine', '3-alpine3.13', '3-alpine']
      alpine3.11 not found
      3-alpine3.11 not found



### PHP-FPM
### php:7.3-fpm-alpine3.9 - NEEDS ATTENTION

Docker Hub - https://hub.docker.com/_/php
News - https://www.php.net/
Releases - https://www.php.net/releases/index.php

    7-fpm
      fpm != 7-fpm
        ['fpm-buster', 'fpm', '8.0.3-fpm-buster', '8.0.3-fpm', '8.0-fpm-buster', '8.0-fpm', '8-fpm-buster', '8-fpm']

    7.4-fpm
      7-fpm = 7.4-fpm

    7.4-fpm-alpine
      fpm-alpine != 7-fpm-alpine
        ['8-fpm-alpine3.13', '8-fpm-alpine', 'fpm-alpine3.13', 'fpm-alpine', '8.0.3-fpm-alpine3.13', '8.0.3-fpm-alpine', '8.0-fpm-alpine3.13', '8.0-fpm-alpine']
      7-fpm-alpine = 7.4-fpm-alpine

    7.4-fpm-alpine3.11
      fpm-alpine != fpm-alpine3.11
        ['8-fpm-alpine3.13', '8-fpm-alpine', 'fpm-alpine3.13', 'fpm-alpine', '8.0.3-fpm-alpine3.13', '8.0.3-fpm-alpine', '8.0-fpm-alpine3.13', '8.0-fpm-alpine']
      fpm-alpine3.11 not found
      7-fpm-alpine3.11 = 7.4-fpm-alpine3.11



## Application Frameworks

### NGINX
### nginx:1.14-alpine - NEEDS ATTENTION

Docker Hub - https://hub.docker.com/_/nginx
News - http://nginx.org/
Releases - http://nginx.org/en/CHANGES

    1
      latest = 1

    1.17
      1 != 1.17
        ['1', 'mainline', 'latest', '1.19.7', '1.19.7', '1.19']

    1.17 Alpine
      alpine = 1-alpine
      1-alpine != 1.17-alpine
        ['mainline-alpine', 'mainline-alpine', 'alpine', '1.19.7-alpine', '1.19-alpine', '1-alpine']



## Databases

### MariaDB
### mariadb:10.3-bionic - NEEDS ATTENTION

Docker Hub - https://hub.docker.com/_/mariadb
News - https://mariadb.org/category/announcement/
Releases - https://mariadb.com/kb/en/mariadb-server/

    10
      latest = 10

    10.4
      10 != 10.4
        ['latest', 'focal', '10.5.9-focal', '10.5.9', '10.5-focal', '10.5', '10-focal', '10']

    10.4 Bionic
      10.4 != 10.4-bionic
        ['10.4.18-focal', '10.4.18', '10.4-focal', '10.4']



### MySQL
### mysql:8.0

Docker Hub - https://hub.docker.com/_/mysql
News - https://www.mysql.com/news-and-events/
Releases - https://dev.mysql.com/doc/relnotes/mysql/8.0/en/

    8
      latest = 8

    8.0
      8 = 8.0



## DevOps Tools

### Jenkins
### jenkins/jenkins:2.190.1-alpine - NEEDS ATTENTION

Docker Hub - https://hub.docker.com/r/jenkins/jenkins
News - https://jenkins.io/node/
Releases - https://jenkins.io/changelog-stable/

    2.204.2
      lts != 2.204.2
        ['2.263.4-lts', 'lts', '2.263.4']

    2.204.2 Slim
      lts-slim != 2.204.2-slim
        ['2.263.4-lts-slim', 'lts-slim', '2.263.4-slim']

    2.204.2 Alpine
      lts-alpine != 2.204.2-alpine
        ['2.263.4-lts-alpine', 'lts-alpine', '2.263.4-alpine']




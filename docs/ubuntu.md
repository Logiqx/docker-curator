## Ubuntu

### System Packages

Most of my projects use Alpine or Debian (slim) images but the Jupyter Notebook project is based on Ubuntu.

Ubuntu packages are installed using "apt-get".



#### mysql-client

mysql-client is required when working on the following projects:

- wca-compose (dev/notebook)



#### gcc

gcc is required when working on the following projects:

- wca-compose (dev/notebook)
  - scw-comp uses [python-Levenshtein](pip/python-Levenshtein.md) which requires gcc to be installed


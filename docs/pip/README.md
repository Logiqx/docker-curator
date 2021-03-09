## PIP

### Introduction

I always specify major and minor release numbers when using "pip install" inside a Dockerfile:

```
pip install --no-cache-dir beautifulsoup4==4.8.*
```

Another valid option would be to specify the major release:

```
pip install --no-cache-dir beautifulsoup4==4.*.*
```

Notes:

- I don't default to the latest because major releases it may contain breaking changes (e.g. dropping support for .xlsx in [xlrd](https://pypi.org/project/xlrd/#description) 2.0).

- I don't specify patch releases (e.g. 0.11.2) because they are too specific and some projects yank them such as [python-Levenshtein](https://pypi.org/project/python-Levenshtein/#history).



### Packages

#### XML / HTML

- [lxml](lxml.md)
- [beautifulsoup4](beautifulsoup4.md)



#### Excel

- [xlrd](xlrd.md)



#### SQL

- [sqlparse](sqlparse.md)
- [PyMySQL](sqlparse)



#### Data Cleansing

- [python-Levenshtein](python-Levenshtein.md)



#### Data Science

- [numpy](numpy.md)
- [scipy](scipy.md)
- [matplotlib](matplotlib.md)



#### DevOps

- [awscli](awscli.md)



#### Web Requests

- [requests](requests.md)
- [google](google.md)


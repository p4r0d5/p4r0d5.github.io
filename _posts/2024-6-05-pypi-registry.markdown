---
layout: post
title:  "pypi nexus registry"
date:   2024-06-05 14:38:00 +0200
categories: python nexus registry
---

# Download example

```
pip install numpy==1.26.1 --index-url
https://user:password@nexus.registry/repository/pypi-public/simple/
```

# Upload example using twine
Configure the twine profile file located in $HOME/.pypirc with path and the credentials.
```
[distutils]
index-servers = nexus
[nexus]
repository: https://yourregistrypath
username: username
password: password
```
Upload:
```
twine upload --repository nexus tzdata-2023.3-py2.py3-none-any.whl
```
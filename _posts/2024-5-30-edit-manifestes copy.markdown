---
layout: post
title:  "edit manifests with yq"
date:   2024-05-30 15:19:00 +0200
categories: bash kubernetes
---

delete
```
yq 'del(.status,.metadata.creationTimestamp,.metadata.resourceVersion,.metadata.uid, .spec.hard."requests.storage")' yrmanifest.yaml
```
modify
```
yq '.metadata.name = "pods-quota"' -i yrmanifest.yaml
```
add content
```
yq '.spec.scopes = []' -i yrmanifest.yaml
yq '.spec.scopes += ["NotTerminating"]' -i yrmanifest.yaml
```



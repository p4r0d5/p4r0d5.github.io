---
layout: post
title:  "awx curl a webook"
date:   2022-08-31 10:55:00 +0200
categories: awx ansible curl
---

```
curl -k -X POST awxwebhookurl' -H 'Content-Type: application/json' -H 'X-Gitlab-Token: gitlabtoken'
```

curl --noproxy='*' if no_proxy var is not working
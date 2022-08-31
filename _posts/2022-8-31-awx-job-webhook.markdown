---
layout: post
title:  "awx curl a webook"
date:   2022-08-31 10:55:00 +0200
categories: awx ansible curl
---

```
curl -k -X POST 'webohookurl' -H 'Content-Type: application/json' -H 'X-Gitlab-Token: token' --data '{ "tower_webhook_event_guid": "'$(date +%s )'"}'
```

curl --noproxy '*' if no_proxy var is not working
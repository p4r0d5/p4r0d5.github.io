---
layout: post
title:  "awx curl a webook"
date:   2022-08-31 10:55:00 +0200
categories: awx ansible curl
---

```
curl -k -X POST 'webohookurl' -H 'Content-Type: application/json' -H 'X-Gitlab-Token: token' --data '{ "id": "'$(date +%s )'"}'
```

If you use the 'example' extra vars in Ansible
```
--data '{ "id": "'$(date +%s )'","example": "false"}' 
```
you can use it with tower_webhook_payload.example variable.

* note: 'We track GUIDs of webhooks that have been run before and don't allow duplicate GUIDs to run additional jobs...' </br>
  source: [https://github.com/ansible/awx/issues/11753](https://github.com/ansible/awx/issues/11753) 
* if no_proxy var is not working
```
curl --noproxy '*' 
```
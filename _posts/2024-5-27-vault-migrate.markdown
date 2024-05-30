---
layout: post
title:  "migrate vault storage"
date:   2024-05-27 14:45:00 +0200
categories: vault kubernetes
---

Migrate storage from file to raft.
Create migrate.hcl:

```
storage_source "file" {
 path = "/vault/data/"
}
 storage_destination "raft" {
 path = "/vault/data/"
}
cluster_addr = "https://vault-0.vault-internal:8201"
```
then
```
vault operator migrate -config=migrate.hcl
```
change the configmap from file to raft.             
[source](https://stackoverflow.com/questions/74643183/hashicorp-vault-migration-from-storage-type-file-to-raft)

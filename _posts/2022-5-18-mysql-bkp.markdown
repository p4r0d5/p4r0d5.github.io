---
layout: post
title:  "at"
date:   2022-03-18 14:11:00 +0200
categories: aws http
---

* insert
```
#!/bin/bash
#2022parodal
dest="/data/mysqldump"
docker exec mysql mysqldump -u username --password= dbname | gzip -9 > $dest/dbname$(date +%d-%m-%y).sql.gz
find $dest -name "*.sql.gz" -type f -mtime +30 -delete
```
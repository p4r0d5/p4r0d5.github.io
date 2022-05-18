---
layout: post
title:  "mysql bkp"
date:   2022-05-18 11:03:00 +0200
categories: docker mysql bash
---

```
#!/bin/bash
#2022parodal
dest="/data/mysqldump"
docker exec mysql mysqldump -u username --password= dbname | gzip -9 > $dest/dbname$(date +%d-%m-%y).sql.gz
find $dest -name "*.sql.gz" -type f -mtime +30 -delete
```
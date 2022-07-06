---
layout: post
title:  "reset sa user"
date:   2022-07-6 9:03:00 +0200
categories: mssql microsoft sa sql light
---
- restart service with -m option
- osql -S MIRAGE\SQLEXPRESS -E
```
alter login sa enable
go
sp_password NULL,'new_password','sa'
go
quit
```
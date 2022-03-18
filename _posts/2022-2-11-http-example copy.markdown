---
layout: post
title:  "http example"
date:   2022-02-11 14:11:00 +0200
categories: aws http
---
```
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from$(hostname -f)</h1>" > /var/www/html/index.html
```


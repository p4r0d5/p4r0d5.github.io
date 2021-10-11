---
layout: post
title:  "Docker SANs go issue"
date:   2021-10-11 15:05:00 +0200
categories: HPE servers centos 
---
# HPONCFG
edit docker.service file. <br>
(centos: /etc/systemd/system/multi-user.target.wants/docker.service)<br>
add in the [Service]
```
# fix SANs issue
Environment="GODEBUG=x509ignoreCN=0"
```
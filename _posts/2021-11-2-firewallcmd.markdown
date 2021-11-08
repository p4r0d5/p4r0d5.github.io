---
layout: post
title:  "firewallcmd"
date:   2021-11-08 14:30:00 +0200
categories: firewallcmd 
---
```
firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="139.191.142.126/32" port protocol="tcp" port="22" accept'
firewall-cmd --reload
firewall-cmd --list-all
```
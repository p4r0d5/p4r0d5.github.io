---
layout: post
title:  "firewallcmd"
date:   2022-1-21 15:30:00 +0200
categories: firewallcmd 
---
```
firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="x.x.x.x/32" port protocol="tcp" port="xxxx" accept'
firewall-cmd --reload
firewall-cmd --list-all
firewall-cmd --permanent --remove-rich-rule ''
```
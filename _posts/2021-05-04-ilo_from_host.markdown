---
layout: post
title:  "ILO management from host"
date:   2021-05-24 16:21:00 +0200
categories: HPE servers centos 
---
# HPONCFG
Hewlett Packard Enterprise offers support forthe iLO features available on ProLiant servers with the HPONCFG utility.<br>

HPONCFG is an online configuration tool used to set up and reconfigure iLO without requiring a reboot of the server operating system. The utility runs in a command-line mode and must be executed from an operating system command line on the local server. HPONCFG enables user to initially configure features exposed through the RBSU or iLO.<br>
https://support.hpe.com/hpesc/public/docDisplay?docId=emr_na-a00007610en_us
<br>
```
yum install libxslt
wget https://downloads.linux.hpe.com/SDR/repo/mcp/centos/6/x86_64/10.30/hponcfg-4.6.0-0.x86_64.rpm
yum install localinstall hponcfg-4.6.0-0.x86_64.rpm
```

https://downloads.linux.hpe.com/SDR/repo/mcp/centos/6/x86_64/10.30/
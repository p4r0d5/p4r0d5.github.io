---
layout: post
title:  "Swarm-tcp-checksums issue"
date:   2021-11-02 9:11:00 +0200
categories: swarm-tcp-checksums docker vmware
---
Docker Swarm Overlay Network ICMP Works, But Not Anything Else:
https://stackoverflow.com/questions/66251422/docker-swarm-overlay-network-icmp-works-but-not-anything-else

```
ethtool -K <interface> tx off
```
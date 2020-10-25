---
layout: post
title:  "edgeos syslog to graylog"
date:   2020-07-03 07:35:34 +0200
categories: jekyll update
---
edit rsys log file:
/etc/rsyslog.d/vyatta-log.conf

{% highlight bash %}
*.*     @graylogipaddress:1514;RSYSLOG_SyslogProtocol23Format
*.notice;local7.debug   -/var/log/messages
{% endhighlight %}

service rsyslog restart
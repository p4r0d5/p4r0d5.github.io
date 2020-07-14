---
layout: post
title:  "fail2ban working with a reverse proxy"
date:   2020-07-13 17:58:34 +0200
categories: jekyll update
---


add this iptables rule to ban the x-forwarded ip address:
{% highlight bash %}
iptables -I INPUT 1 -p tcp --dport 8080 -m string --algo bm --string 'X-Forwarded-For: remoteip' -j DROP
{% endhighlight %}
(delete)
{% highlight bash %}
iptables -L -n --line-numbers|more
iptables -D INPUT 1
{% endhighlight %}

source: https://centos.tips/fail2ban-behind-a-proxyload-balancer/
---
layout: post
title:  "using a private registry in kubernetes"
date:   2020-07-13 16:00:34 +0200
categories: jekyll update
---
create a secret with the credentials:
{% highlight yaml %}
*cat ~/.docker/config.json | base64
{% endhighlight %}
add the encoded credentials to a my-secret.yaml:
{% highlight bash %}
apiVersion: v1
kind: Secret
metadata:
 name: registrypullsecret
data:
 .dockerconfigjson: <base-64-encoded-json-here>
type: kubernetes.io/dockerconfigjson
{% endhighlight %}
create the secret:
{% highlight bash %}
kubectl create -f my-secret.yaml
{% endhighlight %}

than add the secrets in the deployment yaml file:
{% highlight bash %}
imagePullSecrets:
 — name: registrypullsecret
{% endhighlight %}

source: https://blog.cloudhelix.io/using-a-private-docker-registry-with-kubernetes-f8d5f6b8f646
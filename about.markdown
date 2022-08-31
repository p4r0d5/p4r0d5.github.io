---
layout: page
title: About
permalink: /about/
---

This is a collection of notes based on Jekyll [jekyllrb.com](https://jekyllrb.com/)

You can find the source code for Minima at GitHub:
[jekyll][jekyll-organization] /
[minima](https://github.com/jekyll/minima)

You can find the source code for Jekyll at GitHub:
[jekyll][jekyll-organization] /
[jekyll](https://github.com/jekyll/jekyll)


[jekyll-organization]: https://github.com/jekyll

How to upgrade jekyll:
```
docker run -it --rm \
-e http_proxy=http://autoproxy.cec.eu.int:8012 \
-e https_proxy=http://autoproxy.cec.eu.int:8012 \
-v $(pwd):/data \
-w /data \
ruby:latest \
bundle update
```
then commit.

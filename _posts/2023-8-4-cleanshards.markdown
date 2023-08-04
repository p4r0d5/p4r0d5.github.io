---
layout: post
title:  "clean elasticsearch shards"
date:   2023-08-04 10:08:34 +0200
categories: elasticsearch elastic
---
## check status

``` bash
curl -XGET localhost:9200/_cat/shards?h=index,shards,state,prirep,unassigned.reason | grep UNASSIGNED
```

## remove unussigned shards

``` bash
curl -XGET http://localhost:9200/_cat/shards | grep UNASSIGNED | awk {'print $1'} | xargs -i curl -XDELETE "http://localhost:9200/{}"
```
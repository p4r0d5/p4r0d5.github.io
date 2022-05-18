---
layout: post
title:  "curator"
date:   2020-09-28 15:21:00 +0200
categories: curator elastic elasticsearch
---
# curator
Elasticsearch Curator helps you curate, or manage, your Elasticsearch indices and snapshots. <br>
Reference: https://www.elastic.co/guide/en/elasticsearch/client/curator/current/index.html
<br>
Example:<br>
```
curator_cli --host elasticsearch delete_indices --filter_list '[{"filtertype":"age","source":"creation_date","direction":"older","unit":"days","unit_count":1},{"filtertype":"pattern","kind":"prefix","value":"logstash"}]'
```

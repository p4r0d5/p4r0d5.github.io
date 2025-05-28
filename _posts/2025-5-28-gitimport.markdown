---
layout: post
title:  "git import"
date:   2025-05-28 11:55:00 +0200
categories: git
---

## Gitlab
before proceed.     
- new branch master, set it as default and remove main, if requirede.       
- remove permissions on signed code      
- remove permissions on branches     

## Import
```
git clone --bare https://yourrepository.git
cd yourrepository
git push --mirror https://newrepository.git
```

## Gitlab
set back the correct settings         


---
layout: post
title:  "mkdocs-material"
date:   2021-10-26 14:44:00 +0200
categories: mkdocs-material docker
---
https://hub.docker.com/r/squidfunk/mkdocs-material/

```
# Project information
site_name: Test Site
site_description: Test Site Description
site_author: Me

# Theme and overrides, i.e. language partial
theme: material

# Extensions
markdown_extensions:
  - markdown.extensions.admonition
  - markdown.extensions.codehilite(guess_lang=false)
  - markdown.extensions.def_list
  - markdown.extensions.footnotes
  - markdown.extensions.meta
  - markdown.extensions.toc(permalink=true)
  - pymdownx.arithmatex
  - pymdownx.betterem(smart_enable=all)
  - pymdownx.caret
  - pymdownx.critic
  - pymdownx.details
  - pymdownx.emoji:
      emoji_generator: !!python/name:pymdownx.emoji.to_svg
  - pymdownx.inlinehilite
  - pymdownx.magiclink
  - pymdownx.mark
  - pymdownx.smartsymbols
  - pymdownx.superfences
  - pymdownx.tasklist(custom_checkbox=true)
  - pymdownx.tilde

# Page tree
pages:
  - Home: getting-started/index.md
  - Architecture: getting-started/index.md
  - Parent Item:
    - Sub Item 1: getting-started/subitem1.md
    - Sub Item 2: getting-started/subitem2.md
    - Sub Item 3: getting-started/subitem3.md
```
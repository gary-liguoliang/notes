---
layout: post 
title: Jekyll notes for - Disqus & google_analytics
tags:
- jekyll
---


## Comment with Disqus

updated `_config.yml` with: 

```yaml
disqus:
  shortname: <short-name>
```
**issue with the default theme(Minima): We were unable to load Disqus.**
however it seems that the code in [default jekyll theme minima/disqus_comments.html](https://github.com/jekyll/minima/blob/master/_includes/disqus_comments.html) is not working with my Disqus. 

**solution:**

created [_includes/disqus_comments.html](https://github.com/guoliang-dev/guoliang-dev.github.io/blob/master/_includes/disqus_comments.html) with the code copied from Disque. 

## Google analytics 

updted `_config.yml` with:

```yaml
google_analytics: <UA-CODE>
```


for more config comments: [barryclark/jekyll-now/blob/master/_config.yml](https://github.com/barryclark/jekyll-now/blob/master/_config.yml)

---
layout: post
title: up and running with Jekyll
tags:
- jekyll
---

## Config & Enhancement
**add support for tags**
http://blog.meinside.pe.kr/Adding-tag-cloud-and-archives-page-to-Jekyll/

**add 'edit' link**
e.g. 
```html
<a href="https://github.com/repo/folder/edit/gh-pages/{{ page.path }}">
Edit this page on GitHub
</a>
```

## Usage Notes
**':' in the title**
please avoid to use ':' dirtectly in the post meta data. e.g. tile, tag, etc,. 
if you have to use ':', use ```&#58;```

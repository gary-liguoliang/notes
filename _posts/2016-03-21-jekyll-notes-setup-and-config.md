---
layout: post
title: up and running with Jekyll
tags:
- jekyll
---

## Bais Blog features

**Tags**

[How to implement Tags at Jekyll website](http://pavdmyt.com/how-to-implement-tags-at-jekyll-website/)

**Paging**

[Pagination](https://jekyllrb.com/docs/pagination/) 

**Feed**

[Jekyll-feed](https://github.com/jekyll/jekyll-feed)

**sitemap**

[jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap)

**comments**
[disqus](https://disqus.com/)


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

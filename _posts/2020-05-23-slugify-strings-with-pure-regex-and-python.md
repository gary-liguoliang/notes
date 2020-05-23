---
layout: post
title:  "Slugify strings with pure Regex and Python"
date:  20200523 18:07:03 +0800
categories: default 
tags:
---

There are many libs to do slugify, that's cool. but if you just want to slugify simple strings without any dependency, you may want to try:

```
>>> s="Is this is a good title?"
>>> re.sub("[-]+", "-", re.sub("[^a-zA-Z0-9]", "-", s)).lower()

'is-this-is-a-good-title-'
```

purely simple `regex` (yes, I agree, I'm bad at regex, so I copy pasted some from stackoverflow): 

 - `re.sub("[^a-zA-Z0-9]", "-", s)` to replace unknown chars to `-`
 - `re.sub("[-]+", "-", s)` to replace continuous `-`


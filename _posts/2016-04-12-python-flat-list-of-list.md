---
layout: post
title: Python flat a list of list
tags:
 - python
---

```python
>>> l=[[1, 2, 3], [4, 5, 6]]
>>> [i for sublist in l for i in sublist]
[1, 2, 3, 4, 5, 6]
```

http://stackoverflow.com/questions/952914/making-a-flat-list-out-of-list-of-lists-in-python

---
layout: post
title: Python flat a list of list
---

```python
>>> l=[[1, 2, 3], [4, 5, 6]]
>>> [i for sublist in l for i in sublist]
[1, 2, 3, 4, 5, 6]
```

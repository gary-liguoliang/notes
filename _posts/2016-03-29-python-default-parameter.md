---
layout: post
title: Python warning - mutable object as default parameter
tags:
- python
---

### Issue
**list as default parameter**

```python
def f(a, L=[]):
    L.append(a)
    return L

print f(1)
print f(2)
print f(3)
```

**output**

```python
[1]
[1, 2]
[1, 2, 3]
```

### suggestion / solution

```python
def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L
```

>Important warning: The default value is evaluated only once. This makes a difference when the default is a mutable object such as a list, dictionary, or instances of most classes. For example, the following function accumulates the arguments passed to it on subsequent calls:
check out more details: https://docs.python.org/2/tutorial/controlflow.html#default-argument-values

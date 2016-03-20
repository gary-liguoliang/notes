---
layout: default
title: Fluent Python 
---

Fluent Python 
----

**string to array of char**

```python
>>> s = 'abcde'
>>> list(s)
['a', 'b', 'c', 'd', 'e']
```

**remove item from array**

```python
>>> a
['a', 'b', 'c', 'd', 'e']
>>> a.remove('c')
>>> a
['a', 'b', 'd', 'e']
```

**Print array of numbers to one line string**

```python
>>> a=[1, 2, 3]
>>> print a
[1, 2, 3]
>>> for i in a:
...     print i,
... 
1 2 3
>>> print ' '.join(a)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: sequence item 0: expected string, int found
>>> print ' '.join(map(str, a))
1 2 3
```


**char - lowercase / uppercase**

```python
def swap_case(input):
    output = []
    for c in input:
        output.append(str.upper(c) if c.islower() else str.lower(c))
    return''.join(output) 
```


**python division**

```python
>>> 4/3
1
>>> 4/3.0
1.3333333333333333
>>> 4/float(3)
1.3333333333333333
>>> 
>>> from __future__ import division
>>> 4/3
1.3333333333333333
>>> 4//3
1
```

---
layout: default
title: Fluent Python 
---

Fluent Python 
----

# collections

## list / array

### string to list 
**string to array of char**

```python
>>> s = 'abcde'
>>> list(s)
['a', 'b', 'c', 'd', 'e']
```

### remove / print
**remove item from array**
```python
>>> a
['a', 'b', 'c', 'd', 'e']
>>> a.remove('c')
>>> a
['a', 'b', 'd', 'e']
```

**filter**

```python
>>> l = [1, 3, 5, 7, 9]
>>> filter(lambda i: i % 3 == 0, l)
[3, 9]
```

**map**

```python
>>> l
[1, 3, 5, 7, 9]
>>> map(lambda i: i * 2, l)
[2, 6, 10, 14, 18]
```

**print array of numbers to one line string**

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

## set
```python
>>> s1 = set('abc')
>>> s2 = set(['a', 'c', 'e'])
>>> s1.add('f')
>>> s1
set(['a', 'c', 'b', 'f'])
>>> s2
set(['a', 'c', 'e'])

>>> s1.update(['x', 'y'])
>>> s1
set(['a', 'c', 'b', 'f', 'y', 'x'])

>>> s1
set(['a', 'c', 'b', 'f', 'y', 'x'])
>>> s2
set(['a', 'c', 'e'])
>>> 
>>> s1 | s2
set(['a', 'c', 'b', 'e', 'f', 'y', 'x'])
>>> 
>>> s1 & s2
set(['a', 'c'])
>>> 
>>> s1 - s2
set(['y', 'x', 'b', 'f'])
>>> 
>>> s2 - s1
set(['e'])
```


# String

**char - lowercase / uppercase**

```python
def swap_case(input):
    output = []
    for c in input:
        output.append(str.upper(c) if c.islower() else str.lower(c))
    return''.join(output) 
```

# math

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

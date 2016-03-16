Fluent Python 
----

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

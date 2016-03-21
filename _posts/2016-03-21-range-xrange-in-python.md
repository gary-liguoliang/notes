---
layout: default
title: range, xrange in python
---

I made a stupid mistake today when I try to travel for the end of an array to the begining using:
```python for i in xrange(len(ar) - 1, -1) ```

**I should not assume that I understood the API clearly, I should read the manual before I start using it!**

**[range](https://docs.python.org/2/library/functions.html?highlight=range#range)**:
> range(stop)
> range(start, stop[, step])
> This is a versatile function to create lists containing arithmetic progressions. It is most often used in for loops. The arguments must be plain integers. If the step argument is omitted, it defaults to 1. If the start argument is omitted, it defaults to 0. 


**[xrange](https://docs.python.org/2/library/functions.html#xrange)**:

> This function is very similar to range(), but returns an xrange object instead of a list. This is an opaque sequence type which yields the same values as the corresponding list, without actually storing them all simultaneously. 


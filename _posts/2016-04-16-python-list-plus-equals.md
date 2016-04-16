---
layout: post
title: Python list plus equals (+=) operator 
tages:
 - python
---

what's the output of this code?

```python
def list_equals_plus(l):
    l = l + [3, 4]

def list_plus_equals(l):
    l += [3, 4]

if __name__ == '__main__':
    # pass_by_value_and_reference()
    l1 = [1, 2]
    list_equals_plus(l1)
    print 'after list_equals_plus: %s ' % l1

    l2 = [1, 2]
    list_plus_equals(l2)
    print 'after list_plus_equals: %s' % l2
```

```
after list_equals_plus: [1, 2] 
after list_plus_equals: [1, 2, 3, 4]
```

list '+=' actually will extend the original list insead of creating a new one.
[Why does += behave unexpectedly on lists?](http://stackoverflow.com/questions/2347265/why-does-behave-unexpectedly-on-lists)

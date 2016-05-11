---
layout: post
title: Pythonic way for loop and if
tags: python
---

```python

nums = [1, 3, 5, 6, 3, 2, 10, 9, 7]

for i in nums:
    if i > 5:
        print '%s' % i

for i in [n for n in nums if n > 5]:
    print '%s' % i

for i in filter(lambda n: n > 5, nums):
    print '%s' % i


def find_all_files(dirpath, pattern):
    result = set()
    for dirpath, dirs, files in os.walk(dirpath):
        for f in fnmatch.filter(files, pattern):
            result.add(os.path.join(dirpath, f))
    return result
            
```

http://stackoverflow.com/questions/6981717/pythonic-way-to-combine-for-loop-and-if-statement
http://stackoverflow.com/questions/2186525/use-a-glob-to-find-files-recursively-in-python

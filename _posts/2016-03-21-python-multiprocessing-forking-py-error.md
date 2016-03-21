---
layout: default
title: Python - multiprocessing forking.py assertionError
---

Lettcue with Python (< 2.7.11): multiprocessing\forking.py AssertionError: __main__

**Issue:**
There's an AssertionError when I try to test some mutliprocessing features using lettuce 0.2.22 and python 2.7.10
error details:

```python
File "<string>", line 1, in <module>
File "C:\Python27\Lib\multiprocessing\forking.py", line 380, in main
  prepare(preparation_data)
  File "C:\Python27\Lib\multiprocessing\forking.py", line 488, in prepare
    assert main_name not in sys.modules, main_name
AssertionError: __main__
```

**Solution**

 - **upgrade to python 2.7.11** becuase this is a fixed bug: https://bugs.python.org/issue10128; or
 - **use a wrapper** (.py file name should be not in sys.modules, main_name):

```python
# run_at.py:
__requires__ = 'lettuce==0.2.20'
import sys
from pkg_resources import load_entry_point

if __name__ == '__main__':
    sys.exit(
        load_entry_point('lettuce==0.2.20', 'console_scripts', 'lettuce')()
    )
```

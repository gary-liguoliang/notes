---
layout: post 
title: Specify Python interpreter for Python script in Unix and Windows
tags:
- python
---

given this script: test.py:
```python
#!/usr/bin/python

import sys
print sys.executable
```

what's the output of these following scripts?

```python
./test.py
```

```bash
. venv/bin/activate
(venv) ./test.py
```


```python
. venv/bin/activate
(venv) python test.py
```

outputs:
```
usr/bin/pyton
usr/bin/python
/private/tmp/venv/bin/python
```

the [Unix Shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)) will be used to locate the interpreter when the script triggered directly. 

in the example, Shebang is hard-coded to `/usr/bin/python`, actually there's a [more flexiable way](http://stackoverflow.com/questions/5709616/whats-the-difference-between-these-two-python-shebangs) which uses the `path` to find the interpreter:

```bash
#!/usr/bin/env python
```

it works perfect with the virtualenv. 

### conclusion
**Unix**

if you want to run your python script using a virtual environment on a Unix machine:
 - use `#!/usr/bin/env python` as the Shebang:
 
 ```bash
. venv/bin/activate
(venv) ./test.py
```

- or use the python interpreter directly:

  ```bash
/tmp/venv/bin/python test.py
```

**Windows**

There's no Shebang for Windows, it you run ```test.py```, it always uses the default python interpreter. 
if you want to specify the python interpreter, use it directly:

```bash
c:\tmp\venv\Scripts\python c:\tmp\test.py
```


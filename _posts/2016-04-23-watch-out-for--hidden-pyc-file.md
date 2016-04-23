---
layout: post
title: Python- Watch out for the hidden .pyc file!
tags:
 python
---

###What happend:

1. in a python script, e.g. app.py, an external package named 'py_pk' is imported by: ```from py_pk import abc ``` and it works fine.
2. I did a stupid thing is created a .py in the same package with the name 'py_pk.py', after it failed, I realized that the name will cause issue. 
3. however, the .pyc file is still there. the error message from pycharm is about it cannot find modules from py_pk.py! however it's caused by the .pyc!

###Lesson learned:
1. always try your best to name a file, especially in python! never name a file with the same name as the other module!
2. do a 'ls -al' if you find your IDE keep complaining a file which is not exists. it may caused by the .pyc!

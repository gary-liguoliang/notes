---
layout: post 
title: Python tool - converting java system.out.print to SLF4J
tags:
- coding
- java
---

## requirement
convert all java system.out to SLF4J

## solution
read each java source file, add import, replace `system.out.print(...)` to `logger.info(...)`

Python code:


<script src="https://gist.github.com/guoliang-dev/70284ae11351cabed0132ecf37673c1a.js"></script>

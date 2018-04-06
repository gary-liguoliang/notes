---
layout: post 
title: JVM tuning
tags:
- jvm
---


## How to find a Java Memory Leak

```
 - Start the application and wait until it get to "stable" state, when all the initialization is complete and the application is idle.
 - Run the operation suspected of producing a memory leak several times to allow any cache, DB-related initialization to take place.
 - Run GC and take memory snapshot.
 - Run the operation again. Depending on the complexity of operation and sizes of data that is processed operation may need to be run several to many times.
 - Run GC and take memory snapshot.
 - Run a diff for 2 snapshots and analyze it.
```
https://stackoverflow.com/questions/40119/how-to-find-a-java-memory-leak]

**FINDING A MEMORY LEAK WITH JPROFILER:**
http://blog.ej-technologies.com/2017/03/finding-memory-leak-with-jprofiler.html


## jvm tuning

Garbage Collection (GC) Tuning Guide
https://confluence.atlassian.com/enterprise/garbage-collection-gc-tuning-guide-461504616.html#GarbageCollection(GC)TuningGuide-TurnonGClogging


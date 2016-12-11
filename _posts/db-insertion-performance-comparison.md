---
layout: post 
title: Database insertion performance comparison between H2 and MySQL using JDBC 
tags:
- coding
- Database
- MySQL
- H2
- JDBC
---


## Why?
I recommened my friend to use H2(Embedded) to process data from flat files in a java project. however, I was told that the data loading is very slow. 
I want to verify this. 

## Testing Scope
 - data insertion using JDBC. data will be generated during insertion. 
 - SQL join

## Result
### Inserting 1M records (Records / Second)
|DB|Pure SQL Insertion|Prepared Statement|Prepared Statement - BatchSize:50|
|----| ----:|-----:|----:|
|H2 - FileBased|62,305|104,866|107,469|
|H2 - InMemory|54,630|75,392|79,859|
|MySQL|6,835|6,727|7,009|


### Inserting 10M (Prepared Statement AutoCommit)

|DB|Duration|
|----|----:|
|H2 - FileBased|102,176|
|MySQL|7,526|


### Joining - 1M records join with 1M records

|DB|Join Duration (MillionSeconds)|
|---|----:|
|H2 - FileBased|16554|
|H2 - InMemory|2490|
|MySQL|9140|


## Conclusion
**Insertion**
 - PreparedStatement can increase the insertion performance
 - Insert to FileBased embedded H2 database is faster than InMemory H2
 - Joining in InMemory H2 database is faster than MySQL and FileBased H2
 - data insertion to a embedded H2(file-based & in-memory) is faster than MySQL

## Details
[https://github.com/guoliang-dev/db-performance-comparison](https://github.com/guoliang-dev/db-performance-comparison)

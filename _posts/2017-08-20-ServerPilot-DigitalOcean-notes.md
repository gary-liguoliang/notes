---
layout: post 
title: ServerPilot-DigitalOcean notes
tags:
- ServerPilot
- DigitalOcean
---

## Logs
 - [**where's the http access logs?**](https://serverpilot.io/community/articles/where-to-find-your-log-files.html)
```
/srv/users/serverpilot/log/APPNAME/APPNAME_apache.access.log
```
 - [**how to sort by source IP address?**](https://stackoverflow.com/questions/18682308/sort-uniq-ip-address-in-from-apache-log)
 ```
 cat access.log | awk '{print $1}' | sort -n | uniq -c | sort -nr | head -20
 ```
## Blocking IP

 - [**how to block IP address?**](https://serverfault.com/questions/592061/block-range-of-ip-addresses#)
 ```
 sudo iptables -I INPUT -s ip.address.1.2 -j DROP
 ```

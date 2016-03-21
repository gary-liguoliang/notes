---
layout: post 
title: reset mysql root password
tags:
- mysql
- database
---

1. stop mysql: http://stackoverflow.com/questions/18733944/ubuntu-cant-stop-mysqld
2. reset password: https://www.digitalocean.com/community/questions/setup-mysql-on-ubuntu-droplet-getting-error-error-1045-28000-access-denied-for-user-root-localhost-using-password-yes

**where to store the password of 'root'?**
> use ~/.my.cnf to store _User _specific options_
```
[client]
user=root
password=somepassword
```

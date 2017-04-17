---
layout: post 
title: how to setup Ubuntu 14 services 
tags:
- Ubuntu
---

1. ```vi /etc/init/slackbot.conf```
2. add: 
```
start on runlevel [2345]
stop on runlevel [!2345]
script
        /opt/slackbot/venv/bin/python /opt/slackbot/bot/run.py
        others...
end script
```
3. add it to `init.d`

```
ln -s /etc/init/slackbot.conf /etc/init.d/slackbot
```

4. ```sudo service slackbot status/start/stop```

- https://askubuntu.com/questions/351879/how-to-create-a-service-on-ubuntu-upstart
- https://blog.frd.mn/how-to-set-up-proper-startstop-services-ubuntu-debian-mac-windows/

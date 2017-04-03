---
layout: post 
title: Maven deploy error&#58;return code is 502, ReasonPhrase&#58;Bad Gateway
tags:
- maven
---

## Failed to execute goal org.apache.maven.plugins:maven-deploy-plugin: Return code is: 502, ReasonPhrase: Bad Gateway

it may not related to any network / proxy configuration. check your maven security setup: 
https://maven.apache.org/guides/mini/guide-encryption.html

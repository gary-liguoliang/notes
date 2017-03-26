---
layout: post 
title: Sina Weibo OAuth2 Login Notes 新浪微博用户OAuth2登录分析笔记
tags:
- weibo
- javaScript
---

在进行API操作之前, 需要先通过用户授权 并拿到access_token: [API文档](http://open.weibo.com/wiki/Oauth2/authorize)
```
//请求
https://api.weibo.com/oauth2/authorize?client_id=123050457758183&redirect_uri=http://www.example.com/response&response_type=code

//同意授权后会重定向
http://www.example.com/response&code=CODE
```

为了自动化这一过程, 以下是我理解的用户登录:
POST: https://login.sina.com.cn/sso/login.php?client=ssologin.js(v1.4.18)&_=1490516061705&openapilogin=qrcode with:

```
su:dGVzdHVzZXI=
service:miniblog
servertime:1490516059
nonce:JFSCT1
pwencode:rsa2
rsakv:1330428213
sp:9ca9555a1c71f0......bf84e
```

**问题来了, su跟sp是怎么生成的?**


1. Unminfy https://api.weibo.com/oauth2/js/oauth2Web.min.js?version=20160727, found:

```javascript
        var loadSSO = function(callback) {
            if (typeof window.sinaSSOController != "undefined") {
                callback()
            } else {
                $.core.io.scriptLoader({
                    url: "/oauth2/js/sso/ssologin.js",
                    onComplete: function() {
                        setTimeout(callback, 0)
                    }
                })
            }
        };
 ```
 
2. Unmify https://api.weibo.com/oauth2/js/sso/ssologin.js :
 
 ```javascript
request.su = sinaSSOEncoder.base64.encode(urlencode(username));
        if ((me.loginType & rsa) && me.servertime && sinaSSOEncoder && sinaSSOEncoder.RSAKey) {
            request.servertime = me.servertime;
            request.nonce = me.nonce;
            request.pwencode = "rsa2";
            request.rsakv = me.rsakv;
            var RSAKey = new sinaSSOEncoder.RSAKey();
            RSAKey.setPublic(me.rsaPubkey, "10001");
            password = RSAKey.encrypt([me.servertime, me.nonce].join("\t") + "\n" + password)
        } else {
            if ((me.loginType & wsse) && me.servertime && sinaSSOEncoder && sinaSSOEncoder.hex_sha1) {
                request.servertime = me.servertime;
                request.nonce = me.nonce;
                request.pwencode = "wsse";
                password = sinaSSOEncoder.hex_sha1("" + sinaSSOEncoder.hex_sha1(sinaSSOEncoder.hex_sha1(password)) + me.servertime + me.nonce)
            }
        }
        request.sp = password;
 ```

 



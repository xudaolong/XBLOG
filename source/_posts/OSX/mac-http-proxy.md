---
title: mac-http-proxy
date: 2016-09-11
categories: 
- osx
---


==> Pouring privoxy-3.0.24.el_capitan.bottle.1.tar.gz
==> Caveats
To have launchd start privoxy now and restart at login:
  brew services start privoxy
Or, if you don't want/need a background service you can just run:
  privoxy /usr/local/etc/privoxy/config
==> Summary
🍺  /usr/local/Cellar/privoxy/3.0.24: 51 files, 1.6M

启动 http代理

/usr/local/Cellar/privoxy/3.0.24/sbin/privoxy /usr/local/etc/privoxy/config 


# 测试是否抵达地址

curl --connect-timeout 2 -x 127.0.0.1:8118 http://www.baidu.com





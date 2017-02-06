---
title: 配置-VPN-常用操作
date: 2016-09-11
categories: 
- vps
---

> 启动
service iptables restart
chkconfig iptables on

service pptpd restart
chkconfig pptpd on
clear

> 添加用户
vi /etc/ppp/chap-secrets


> https://blog.linuxeye.com/412.html

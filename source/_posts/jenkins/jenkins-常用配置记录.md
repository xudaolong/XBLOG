---
title: jenkins-常用配置记录
date: 2016-09-11
categories: 
- jenkins
---

> 设定默认端口

```

sudo defaults write /Library/Preferences/org.jenkins-ci httpPort 7070

```

> 启动

```

sudo launchctl unload /Library/LaunchDaemons/org.jenkins-ci.plist

```

> 关闭

```

sudo launchctl load /Library/LaunchDaemons/org.jenkins-ci.plist

```

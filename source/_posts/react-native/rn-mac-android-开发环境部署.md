---
title: rn-mac-android-开发环境部署
date: 2016-09-11
categories: 
- react-native
---

> 参考资源

http://facebook.github.io/react-native/docs/getting-started.html#content
http://reactnative.cn/docs/0.37/getting-started.html
http://blog.csdn.net/gz_jero/article/category/6223090


> 遇到的问题如下:

1. `adb command not found`:adb命令存在platform-tools中;

解决:在.bash_profile 文件中配置如下.
```
export ANDROID_HOME=~/Library/Android/sdk
export PATH=${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools
```

2.关于sdk的安装慢(使用shadowscoks),安装失败,建议直接使用sdk manager进行安装.
```

android sdk

```

3.关于选取sdk,选择

![](http://upload-images.jianshu.io/upload_images/80378-5d0bab5baa5b17b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

可解决问题:No system images installed for this target
```
If you see "No system images installed for this target." under CPU/ABI, go back to your "SDK Manager" and click on "Show Package Details" under "SDK Platforms". You will then be able to install any missing system images, such as "Google APIs Intel Atom (x86)".
```




---
title: rn-mac-android-开发日常记录
date: 2016-09-11
categories: 
- react-native
---

> react-native 调试参考

http://blog.csdn.net/quanqinyang/article/details/52215652

>知识点

1.React Native中的尺寸都是无单位的，表示的是与设备像素密度无关的逻辑像素点。
```
<View>
	<View style={{width: 50, height: 50, backgroundColor: 'powderblue'}} />
	<View style={{width: 100, height: 100, backgroundColor: 'skyblue'}} />
	<View style={{width: 150, height: 150, backgroundColor: 'steelblue'}}/>
</View>
```

2.使用``flex: 1``来指定某个组件扩张以撑满所有剩余的空间。如果有多个并列的子组件使用了``flex: 1``，则这些子组件会``平分``父容器中剩余的空间。如果这些并列的子组件的flex值不一样，则谁的值更大，谁占据剩余空间的比例就更大（即占据剩余空间的比等于并列组件间flex值的比）默认: ``横向并列``
```
<View style={{flex: 1}}>
	<View style={{flex: 1, backgroundColor: 'powderblue'}}/>
	<View style={{flex: 2, backgroundColor: 'skyblue'}}/>
	<View style={{flex: 3, backgroundColor: 'steelblue'}}/>
</View>
```

![](http://upload-images.jianshu.io/upload_images/80378-3c707360d005ae8c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.关于Flexbox
``flexDirection``、``alignItems``和``justifyContent``:
React Native中的Flexbox的工作原理和web上的CSS基本一致，当然也存在少许差异。首先是默认值不同：**flexDirection**的默认值是column而不是row，**alignItems**的默认值是stretch而不是flex - start，以及flex只能指定一个数字值。


![flexDirection](http://upload-images.jianshu.io/upload_images/80378-8854621e184fde69.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![flexWarp](http://upload-images.jianshu.io/upload_images/80378-3e01d184f940c2d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![justifyContent](http://upload-images.jianshu.io/upload_images/80378-393e92ff31c22867.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![alignItems](http://upload-images.jianshu.io/upload_images/80378-8bba57f0041fae31.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![alignContent](http://upload-images.jianshu.io/upload_images/80378-1b41103e2f83d4b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

具体的样式列表:
http://reactnative.cn/docs/0.37/layout-props.html

> 双数据的绑定:主要解决的是该变量增加和删除带来的重复地对相关组件的渲染的影响.

> 关于TextInput:

``onChangeText``、``onSubmitEditing``、``onSubmitEditing``...
更多查看:http://reactnative.cn/docs/0.37/textinput.html

> android 模拟器 获取不了网络/没有wifi

```
adb shell
getprop
```

然后发现:模拟器的DNS地址
![](http://upload-images.jianshu.io/upload_images/80378-22de6a6484530f18.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/80378-44d740474d8e6ad3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

进行设置:**在模拟器的Setting->无线网络设置里，把“启用数据流量”勾选上，让模拟器的TopTar上出现3G图标**,另外在重启模拟器后设置的property会丢失，就需要重新设置一遍，可以使用下面的方法解决：

找到你的SDK目录，里面有个system-images文件夹，这里保存着系统镜像文件，用文本编辑器打开里面的build.prop文件，在里面加上**net.dns1=DNS**

```
/Users/macbook/Library/Android/sdk/system-images/android-23/google_apis/x86
```

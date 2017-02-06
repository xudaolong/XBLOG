---
title: java-fastjson-解析json配置文件
date: 2016-09-11
categories: 
- java
---

> 需要准备下面工具:

```

fastjson
common-io(文件转化为Stirng)
网址:http://www.bejson.com/json2javapojo/  (JSON字符串转换成Java实体类(POJO))

```

> json格式如下

```

{
  "QRratio": {
    "x": 111,
    "y": 111,
    "width": 4000,
    "height": 4000
  },
  "Interleaved2of5": {
    "x": 111,
    "y": 111,
    "width": 4000,
    "height": 4000
  },
  "comment": "不同分辨率的情况下获取的区域不一样"
}

```

> 生成Java实体类

![bean.png](http://upload-images.jianshu.io/upload_images/80378-f4a3d68c1deb70c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 核心代码块

```

        //配置不同分辨率下不同的QR 和 25 码的配置文件
        InputStream inputStream = new FileInputStream("config/billtype.conf.json");
        String text = IOUtils.toString(inputStream,"utf8");
        Root root = JSON.parseObject(text,Root.class);

```

> 导包

```

import com.alibaba.fastjson.JSON;
import com.xudaolong.bean.config.Root;
import org.apache.commons.io.IOUtils;

import java.io.File;
import java.io.FileInputStream;

```

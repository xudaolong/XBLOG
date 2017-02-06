---
title: java-common-Lang-CharSetUtils
date: 2016-09-11
categories: 
- apache-common
- java
---


> 常用函数如下:

```

static boolean	containsAny(String str, String... set)
接受一个参数集语法,看到evaluateSet, 并确定是否有任何的角色出现在指定的字符串中。
static int	count(String str, String... set)
接受一个参数集语法,看到evaluateSet, 并返回指定数量的字符出现在字符串。
static String	delete(String str, String... set)
接受一个参数集语法,看到evaluateSet, 和删除任何的字符出现在指定的字符串。
static String	keep(String str, String... set)
接受一个参数集语法,看到evaluateSet, 并保持任何的字符出现在指定的字符串。
static String	squeeze(String str, String... set)
根据参数二set提供的字母序列,删除重复的字符

```


> 测试用例

```

/**
 * 文 件 名: TestCharSetUtils
 * 创 建 人: xudaolong
 * 创建日期: 16/7/23 14:09
 * 邮   箱: xudaolong@vip.qq.com
 * 博   客: http://xudaolong.github.io/
 * 修改时间：
 * 修改备注：
 */
public class TestCharSetUtils {

    public static Logger log = Logger.getLogger(TestCharSetUtils.class);

    @Test
    public void TestCharSet() {
        String memo = "xudaollong";
        /**
         * 好像都是些过滤的作用而已
         */
        //是否包含指定的字母列
        log.info(CharSetUtils.containsAny(memo, "a-v"));
        //删除指定的字母列
        log.info(CharSetUtils.delete(memo,"a-c"));
        //仅保留指定字母列
        log.info(CharSetUtils.keep(memo,"c-z"));
        //删除重复值
        log.info(CharSetUtils.squeeze(memo, "l"));
        //计算指定字母数
        log.info(CharSetUtils.count(memo, "l"));
    }


}

```


> 结果

```

2016-07-23 14:41:34 [INFO] true [main] com.xudalong.CharSetUtils.TestCharSetUtils [com.xudalong.CharSetUtils.TestCharSetUtils.TestCharSet(TestCharSetUtils.java:27)]
2016-07-23 14:41:34 [INFO] xudollong [main] com.xudalong.CharSetUtils.TestCharSetUtils [com.xudalong.CharSetUtils.TestCharSetUtils.TestCharSet(TestCharSetUtils.java:29)]
2016-07-23 14:41:34 [INFO] xudollong [main] com.xudalong.CharSetUtils.TestCharSetUtils [com.xudalong.CharSetUtils.TestCharSetUtils.TestCharSet(TestCharSetUtils.java:31)]
2016-07-23 14:41:34 [INFO] xudaolong [main] com.xudalong.CharSetUtils.TestCharSetUtils [com.xudalong.CharSetUtils.TestCharSetUtils.TestCharSet(TestCharSetUtils.java:33)]
2016-07-23 14:41:34 [INFO] 2 [main] com.xudalong.CharSetUtils.TestCharSetUtils [com.xudalong.CharSetUtils.TestCharSetUtils.TestCharSet(TestCharSetUtils.java:35)]

```

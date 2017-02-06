---
title: java-common-Lang-StringUtils
date: 2016-09-11
categories: 
- apache-common
- java
---


> 概述介绍基本的功能

```

IsEmpty/IsBlank(可含有whitespace) - 是否包含文本
Trim/Strip(中间空的保留) - 删除前后空格
Equals/Compare - 比较两个字符串
startsWith - 是否以某字符串开始
endsWith - 是否以某字符串结束
IndexOf/LastIndexOf/Contains - 空字符串检测
IndexOfAny/LastIndexOfAny/IndexOfAnyBut/LastIndexOfAnyBut - 是否包含哪些字符串
ContainsOnly/ContainsNone/ContainsAny - 字符是否仅包含/不含有/任何这些字符串
Substring/Left/Right/Mid - 截取字符串
SubstringBefore/SubstringAfter/SubstringBetween - 提取相对其他字符串
Split/Join - 分割/组合成数组
Remove/Delete - 删除部分字符串
Replace/Overlay - 搜索/替换字符串
Chomp/Chop - 删除最后的字符串
AppendIfMissing - 保持固定后缀
PrependIfMissing - 保持固定前缀
LeftPad/RightPad/Center/Repeat - 左/右/中/重复/地填充
UpperCase/LowerCase/SwapCase/Capitalize/Uncapitalize - 改变字符串的大小写
CountMatches - 计算此字符串在另外一个字符串出现的次数
IsAlpha/IsNumeric/IsWhitespace/IsAsciiPrintable - 检查字符串的类型
DefaultString - 防止输入空值而设定默认值
Rotate - 旋转字符串
Reverse/ReverseDelimited - 逆转一个字符串
Abbreviate - 将字符串省略化
Difference - 字符串间的区别
LevenshteinDistance - 两个字符串的具体值差距


```

> 除去上面那个比较常见的函数外,还有一些高级的...

> Empty : null 、 ""

> Blank : whitespace 、 null 、 ""

```

isNotEmpty/isNotBlank : 确保不为空

isAnyEmpty/isAnyBlank : 是否包含一个空字符串

isNoneEmpty/isNoneBlank : 确保全部是有效值

trimToNull/stripToNull : Blank元素转成 null

trimToEmpty/stripToEmpty : Blank元素转成 "" 

truncate : 按前到后截断

stripAll : 处理多个字符串

stripAccents : 去除音标

equalsIgnoreCase : 忽略大小比较



```

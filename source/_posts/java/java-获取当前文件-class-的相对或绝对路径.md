---
title: java-获取当前文件-class-的相对或绝对路径
date: 2016-09-11
categories: 
- java
---

```
package com.xudaolong.Utils;


import java.io.File;

/**
 * Created by xudaolong on 16/7/12.
 */
public class Path {

    private static final String TAG = "Path";

    /**
     * 创建不存在的目录
     * @param c
     * @param dir
     * @return
     */
    public File rebuildDir(Class c,File dir){

        for (String s : c.getName().split("\\.")) {
            dir = new File(dir, s);
            if (dir.isDirectory() == false)
                dir.mkdirs();
        }

        return dir;
    }

    /**
     * 返回指定的路径为 resources
     *
     * @param c
     * @return
     */
    public String getDataDir(Class c) {

        //获取当前的路径
        File dir = new File(System.getProperty("user.dir"));

        //目录resolve
        dir = new File(dir, "resources");
        dir = this.rebuildDir(c, dir);

        System.out.println(TAG + "::Using data directory::" + dir.toString());
        return dir.toString() + File.separator;

    }

    /**
     * 返回指定相对路径,相对的是user.dir
     * @param c
     * @param desc
     * @return
     */
    public String getDataDir(Class c, String desc) {

        //获取当前的路径
        File dir = new File(System.getProperty("user.dir"));

        //目录resolve
        dir = new File(dir, desc);
        dir = this.rebuildDir(c, dir);

        System.out.println(TAG + "::Using data directory::" + dir.toString());

        return dir.toString() + File.separator;
    }


}

```

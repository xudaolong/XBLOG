---
title: Aspose-barcode-条码和二维码处理
date: 2016-09-11
categories: 
- others
---

> 条码信息和贴士

```

http://china.keyence.com/ss/products/auto_id/barcode_lecture/

```

> 应用背景:公司需要将发票中的二维码和条码一同识别并于相关的订单绑定至数据库

> 初略的第一版

```

package com.xudaolong.bean;

import com.aspose.barcode.*;
import com.aspose.barcoderecognition.BarCodeReadType;
import com.aspose.barcoderecognition.BarCodeReader;
import com.xudaolong.Utils.ImageCutterUtil;

import javax.imageio.ImageIO;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;
import java.util.ArrayList;

/**
 * 文 件 名: AsposeBarcode.java
 * 创 建 人: xudaolong
 * 创建日期: 16/7/12 14:24
 * 邮   箱: xudaolong@vip.qq.com
 * 博   客: http://xudaolong.github.io/
 * 修改时间：
 * 修改备注：
 */

public class AsposeBarcode {

    private static final String TAG = "AsposeBarcode";

    /**
     * 发票信息列表
     */
    private ArrayList<BarcodeInfo> list = new ArrayList();


    public AsposeBarcode() {

    }

    /**
     * 存储扫描发票信息(二维码和二五码)
     */
    class BarcodeInfo {
        private static final String TAG = "BarcodeInfo";

        public BarcodeInfo() {

        }

        private String FileName;
        private String Interleaved2of5;
        private String QR;

        public void clear() {
            this.setFileName("");
            this.setInterleaved2of5("");
            this.setQR("");
        }

        public String getFileName() {
            return FileName;
        }

        public void setFileName(String fileName) {
            this.FileName = fileName;
        }

        public String getQR() {
            return QR;
        }

        public void setQR(String QR) {
            this.QR = QR;
        }

        public String getInterleaved2of5() {
            return Interleaved2of5;
        }

        public void setInterleaved2of5(String interleaved2of5) {
            Interleaved2of5 = interleaved2of5;
        }

        public void checkInfo(BarcodeInfo _info) {
            if (_info.getInterleaved2of5().equals("")) {
                System.out.println(_info.getFileName() + ":: 不能获取 Interleaved2of5 条形码");
            }

            if (_info.getQR().equals("")) {
                System.out.println(_info.getQR() + ":: 不能获取 QR 条形码 ");
            }
        }

        @Override
        public String toString() {
            return "BarcodeInfo{" +
                    "FileName='" + this.getFileName() + '\'' +
                    ", Interleaved2of5='" + this.getInterleaved2of5() + '\'' +
                    ", QR='" + this.getQR() + '\'' +
                    '}';
        }
    }

    /**
     * 获取工具类
     *
     * @return
     */
    public BarCodeBuilder getInstance() {
        return new BarCodeBuilder();
    }

    /**
     * 获取一个普通的QR图片
     *
     * @return
     */
    public BarCodeBuilder getPublicQR(String context, String targetPath) {

        // 初始化
        BarCodeBuilder builder = this.getInstance();

        builder.setCodeText(context);
        builder.setSymbologyType(Symbology.QR);

        // 设置编程模式
        builder.setQREncodeMode(QREncodeMode.Auto);

        // 设置容错率
        builder.setQRErrorLevel(QRErrorLevel.LevelH);

        // 隐藏文字
        builder.setCodeLocation(CodeLocation.None);

        // 翻转
        builder.setRotationAngleF(0);

        builder.setImageHeight(88);
        builder.setImageWidth(88);

        // 保存
        builder.save(targetPath);

        cutQR(targetPath);

        return builder;
    }


    public void cutQR(String sourcePath) {

        try {
            File file = new File(sourcePath);

            BufferedImage image = ImageIO.read(file);

            // 起始坐标，剪切大小
            int x = 14;
            int y = 25;
            int width = 62;
            int height = 62;
            // 参考图像大小
            int clientWidth = 88;
            int clientHeight = 88;

            double destWidth = image.getWidth();
            double destHeight = image.getHeight();

            if (destWidth < width || destHeight < height)
                throw new Exception("源图大小小于截取图片大小!");


            double widthRatio = destWidth / clientWidth;
            double heightRatio = destHeight / clientHeight;

            //修改一下单位
            x = Double.valueOf(x * widthRatio).intValue();
            y = Double.valueOf(y * heightRatio).intValue();
            width = Double.valueOf(width * widthRatio).intValue();
            height = Double.valueOf(height * heightRatio).intValue();

            System.out.println("裁剪大小  x:" + x + ",y:" + y + ",width:" + width + ",height:" + height);

            //获取指定的名字
//            String formatName = getImageFormatName(file);
//            String pathSuffix = "." + formatName;
//            String pathPrefix = getFilePrefixPath(file);
//            String targetPath = pathPrefix + System.currentTimeMillis() + pathSuffix;

            //最后一步进行裁剪到指定的名字

            File destFile = new File(sourcePath);

            ImageCutterUtil.cutImage(file, destFile, x, y, width, height);

        } catch (Exception e) {
            e.printStackTrace();
        }

    }


    /**
     * 读取QR
     *
     * @return
     */
    public ArrayList<BarcodeInfo> ReaderImg(String dest) throws IOException {

        if (dest == null) {
            return null;
        }

        /**
         * 转成 BufferedImage 图像缓存区便于操作
         */
//        BufferedImage bufImg = ImageIO.read(new FileInputStream(dest));

        //创建指定的读取器 25码 和 QR 码
        BarCodeReader reader = new BarCodeReader(dest, BarCodeReadType.QR | BarCodeReadType.Interleaved2of5);

        /**
         * MaxPerformance	1	Finds all the possible good and average quality barcodes. Uses only the fastest algorithms. Enabled by default.
         * MaxQuality	2	Finds all the possible barcodes with good or bad quality. Doesn't return potential barcodes. Uses different fast and slow algorithms.
         * MaxBarCodes	3	Extends MaxQuality. Finds even potential barcodes. Uses extra algorithms which may recognize incorrect barcodes, barcodes on complex background, noisy or damaged barcodes and etc. You may observe extra spurious barcodes.
         * ManualHints	4	User configures hints optionally. Allows you to adjust the balance between speed and quality manually.
         */
        reader.setRecognitionMode(1);

        /**
         * 设定识别超时,有助于提高识别效率
         */
//        reader.setTimeout(3500);

        //暂时存储
        BarcodeInfo _info = new BarcodeInfo();

        //重置
        _info.clear();

        try {
            while (reader.read()) {
                _info.setFileName(reader.getFileName());

                if (reader.getReadTypeName().equals("Interleaved2of5")) {
                    _info.setInterleaved2of5(reader.getCodeText());
                }

                if (reader.getReadTypeName().equals("QR")) {
                    _info.setQR(reader.getCodeText());
                }
            }

            list.add(_info);
            reader.close();
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            _info.checkInfo(_info);
        }

        return list;
    }

}


```


> 测试文件

```

package com.xudaolong.QR;

import com.xudaolong.Utils.Path;
import com.xudaolong.bean.AsposeBarcode;

import java.io.IOException;
import java.util.ArrayList;

/**
 * Created by xudaolong on 16/7/12.
 */

public class TestQR {

    public static void main(String[] args) throws IOException {
        //指定相对的路径
        String path = “/resources/src/com/xudaolong/second”;

        long startTime=System.nanoTime();   //获取开始时间


        ArrayList<String> allFile =  new Path().getAllFile(path);

        for (int i = 0; i < allFile.size(); i++) {
            String _filename = allFile.get(i);
            System.out.println(new AsposeBarcode().ReaderImg(_filename));
        }

        long endTime=System.nanoTime(); //获取结束时间
        System.out.println(“程序运行时间： “+(endTime-startTime)+”ns”);
        
        System.out.println(allFile);

    }

}


```

> 辅助类 Path::用于处理路径的问题

```

package com.xudaolong.Utils;


import java.io.File;
import java.util.ArrayList;

/**
 * Created by xudaolong on 16/7/12.
 */
public class Path {

    private static final String TAG = "Path";

    public static final String CURRFILE = new String(System.getProperty("user.dir"));

    /**
     * 创建不存在的目录
     *
     * @param c
     * @param dir
     * @return
     */
    public File rebuildDir(Class c, File dir) {

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
        //目录resolve
        File _currfile = new File(CURRFILE, "resources");
        _currfile = this.rebuildDir(c, _currfile);

        System.out.println(TAG + "::Using data directory::" + _currfile.toString());
        return _currfile.toString() + File.separator;

    }

    /**
     * 返回指定相对路径,相对的是user.dir
     *
     * @param c
     * @param desc
     * @return
     */
    public String getDataDir(Class c, String desc) {

        File _currfile = new File(CURRFILE, "resources");

        //目录resolve
        _currfile = new File(_currfile, desc);
        _currfile = this.rebuildDir(c, _currfile);

        System.out.println(TAG + "::Using data directory::" + _currfile.toString());

        return _currfile.toString() + File.separator;
    }

    /**
     * 返回绝对路径的文件名组
     *
     * @param floder
     * @return
     */
    public ArrayList<String> getAllFile(String floder) {
        if (floder == null) {
            return null;
        }
        //存储文件名
        ArrayList _allfilename = new ArrayList();

        //获取当前的路径
        File _currfile = new File(CURRFILE);

        //目录resolve
        _currfile = new File(_currfile, floder);

        if (!_currfile.exists()) {
            System.out.println(floder + " not exists");
            return null;
        }

        File _dir[] = _currfile.listFiles();

        for (int i = 0; i < _dir.length; i++) {
            File fs = _dir[i];
            if (fs.isDirectory()) {
                System.out.println(fs.getName() + “ [目录]”);
            } else {
                _allfilename.add(_currfile + “/“ + fs.getName());
            }
        }

        return _allfilename;
    }

}


```







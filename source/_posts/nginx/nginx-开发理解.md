---
title: nginx-开发理解
date: 2016-09-11
categories: 
- nginx
---

> 安装 epel

```

sudo yum install epel-release

```

> 安装 nginx

```

sudo yum install nginx

```

> 启动

```

sudo /etc/init.d/nginx start

```

> 查看 worker_process 数目

```

grep ^processor /proc/cpuinfo | wc -l

```

> 启动

```

nginx

```

> 重启

```

sudo nginx -s reload

```

> 删除

```

pkill nginx 

```

> 安装依赖(默认目录)-->http://nginx.org/en/download.html

```
yum -y install gcc gcc-c++ make libtool zlib zlib-devel openssl openssl-devel pcre pcre-devel
```

> 了解四个部分

```
main（全局设置）、server（主机设置）、upstream（上游服务器设置，主要为反向代理、负载均衡相关配置）和 location（URL匹配特定位置后的设置）
```

> main

```
影响所有的配置
```

> server 

```
域名-IP-端口
```

> upstream

```
反向代理和负载均衡
```

> location

``` 
网页的配置
```



```



-------------main
# 查看配置文件是否正确
sudo nginx -t

# 查看默认的配置
cat /usr/local/etc/nginx/nginx.conf.default

# user 管理用户 用户组
whoami
groups

# worker_processes 占用内核的数量
sysctl -n hw.ncpu

# error_log 路径 模式
mac 路径:/usr/local/var/log/nginx/error.log
centos 路径: /var/log/nginx/error.log
模式类型 : debug/info/notice/warn/error/crit (越不详细)

# pid 路径
mac 路径:/usr/local/var/run/nginx.pid
centos 路径:/var/run/nginx.pid

---------------main

---------------events

# worker_connections number
若提示 worker_connections exceed open file resource limit: 256,可以在main的部分添加 worker_rlimit_nofile 2048;

---------------events

---------------http
http {
 	# 关闭错误页面的nginx版本数字，提高安全性
    server_tokens off;
    include       mime.types;
    default_type  application/octet-stream;

    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    #高效文件传输模式,是否调用sedfile函数输出文件,减少上下文切换,若下载等应用盘则off
    sendfile        on;

    #tcp_nopush     on;

    #长连接超时时间
    keepalive_timeout  65;

    #send_timeout : 响应客户端超时的时间;

    #启动gzip,为了减少网路传输
    gzip on;
    #允许压缩的页面的最小字节数,小于1k的可能越压越大
    gzip_min_length 1k;
    #数据流
    gzip_buffers    4 16k;
    #协议的版本,支持早期的不支持gzip的浏览器
    gzip_http_version 1.0;
    #压缩比,越小越快,越大越耗能;
    gzip_comp_level 6;
    #压缩的类型
    gzip_types text/plain text/css text/javascript application/json application/javascript application/x-javascript application/xml;
    #响应头加上vary
    gzip_vary on;

    # http_proxy 设置
    # 请求文件字节数的大小和缓存区
    client_max_body_size   10m;
    client_body_buffer_size   128k;

    #proxy 时间控制
    proxy_connect_timeout   75;
    proxy_send_timeout   75;
    proxy_read_timeout   75;

    #proxy 缓存设置
    proxy_buffer_size   4k;
    proxy_buffers   4 32k;
    proxy_busy_buffers_size   64k;

    #proxy 临时文件大小
    proxy_temp_file_write_size  64k;
    
    # 确认路径三 centos的路径在 /etc/nginx/
    proxy_temp_path   /usr/local/etc/nginx/proxy_temp 1 2;
    
    # 引入其他的server

    include servers/*;
}
---------------http

 # 关闭错误页面的nginx版本数字，提高安全性
 server_tokens off;



```

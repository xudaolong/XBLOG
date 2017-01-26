# vsftpd 组件

yum -y install vsftpd 

# 查看当前用户

cat /etc/passwd 

# 启动 vsftpd start

service vsftpd start 

# 安装ftp 客户端

yum -y install ftp 

# 尝试登陆

ftp localhost  

# 取消匿名登陆, anonymous_enable=YES ，改为NO

vi /etc/vsftpd/vsftpd.conf 

# 创建用户名修改密码

useradd ftpuser 

passwd ftpuser 

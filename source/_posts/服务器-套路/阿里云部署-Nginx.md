# 开机启动
sudo update-rc.d -f nginx defaults

# 启动
sudo /etc/init.d/nginx start

# 查看配置的文件
nginx -t

# 后台启动
nohup redis-server &

### 使用pip安装server,apt-get install python-pip  pip install shadowsocks

### 创建配置文件config.json
        {
            "server":"0.0.0.0",
            "server_port":7799,
            "local_address": "127.0.0.1",
            "local_port":1080,
            "password":"****",
            "timeout":300,
            "method":"aes-256-cfb",
            "fast_open": false
        }
### ssserver -c /etc/config.json start 启动服务器，也可以指定-d 监控执行程序
参考链接：[上网](http://wuchong.me/blog/2015/02/02/shadowsocks-install-and-optimize/)

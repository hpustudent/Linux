### 安装jdk, `apt-get install openjdk-7-jdk`

### 安装openssl , ` apt-get install libcurl4-openssl-dev`

### 安装tengine, 


    apt-get install gcc libpcre3 libpcre3-dev zlib1g-dev 安装tengine必须的环境  
    wget -c http://tengine.taobao.org/download/tengine-2.2.0.tar.gz
    cd tengine-2.2.0
    ./configure --prefix=/alidata/server/nginx  --prefix是指定路径，默认在/usr/local下
    make
    make install
    /alidata/server/nginx/sbin/ningx

### 使用tengine
1. 直接进入sbin目录下，使用nginx敲击回车，就会启动tengine,访问localhost就会给出提示
2. 如果要想测试一下编辑过的ngxin.conf文件语法是否争取，可以用nginx -t 命令进行测试
3. 如果修改了nginx.conf文件，可以使用nginx -s reload，重新载入nginx配置文件并启动服务器
4. 如果想要停止运行nginx,使用nginx -s stop 停止运行ngxin，-s意思为signal

### 编辑配置文件
1. 在nginx目录下，找到conf目录，找到nginx.conf打开编辑
2. 配置禁止ip或者非法域名访问服务器

        server {
                listen 80 default;
                server_name _;
                return 500;
        }
        
3. 配置反向代理服务器群
   
       upstream baidunodes {
            server 127.0.0.1:8080;
       }

       server {
            listen       80;
            server_name www.baidu.com;

            location / {
                proxy_pass http://baidunodes;
                proxy_set_header Host $http_host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }

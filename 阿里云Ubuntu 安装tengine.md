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

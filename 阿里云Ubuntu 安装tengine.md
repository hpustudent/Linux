### 安装jdk, `apt-get install openjdk-7-jdk`

### 安装openssl , ` apt-get install libcurl4-openssl-dev`

### 安装tengine, 


    wget -c http://tengine.taobao.org/download/tengine-2.2.0.tar.gz
    cd tengine-2.2.0
    ./configure --prefix=/alidata/server/nginx 
    make
    make install
    /alidata/server/nginx/sbin/ningx

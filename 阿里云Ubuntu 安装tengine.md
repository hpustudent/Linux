### 安装jdk, `apt-get install openjdk-7-jdk`

### 安装openssl , ` apt-get install libcurl4-openssl-dev`

### 安装tengine, 


    wget http://tengine.taobao.org/download/tengine-2.0.3.tar.gz
    chmod 755 tengine-2.0.3.tar.gz
    tar -xzvf  tengine-2.0.3.tar.gz
    cd tengine-2.0.3
    ./configure --prefix=/alidata/server/nginx 
    make
    make install
    /alidata/server/nginx/sbin/ningx

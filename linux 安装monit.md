#### centos 安装monit
1. `yum install monit`
2. 编辑配置文件`/etc/monitrc` 修改配置
3. 常用命令
    
   + `monit -t`测试配置文件是否正确  
   + `monit summary`查看摘要信息  
   + `monit status`查看服务运行信息  

4. 安装mmonit

    + `wget -c https://mmonit.com/dist/mmonit-3.7.1-linux-x64.tar.gz`下载安装包    
    + oneinstack 安装mysql  
    + 将db/mmonit-schema.mysql中的sql在mysql创建的数据库中执行，创建相关表  
    + 在conf/server.xml中修改服务器配置，修改  
    
    <Realm url="mysql://username:password@127.0.0.1/mmonit"  minConnections="1" maxConnections="25" reapConnections="1000" />

#### ubuntu 安装monit
1. `apt-get install monit`

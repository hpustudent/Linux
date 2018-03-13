#### centos 安装monit
1. `yum install epel-release`   `yum install monit`
2. 编辑配置文件`/etc/monitrc` 修改配置,`systemctl enable monit`设置开机启动
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

    + 变更系统日期 `date 060610002011` 
    + 启动服务器 `bin/mmonit start` 
    + 还原系统日期 `ntpdate  3.centos.pool.ntp.org` 
    + 加入开机启动 `echo "/usr/local/mmonit/bin/mmonit start">>/etc/rc.d/rc.local` 
    + 默认用户admin 默认密码swordfish  
    + 在monit客户端启用`set mmonit http://monit:monit@192.168.1.10:8080/collector`即可

5.monit 配置邮件提醒

    set mailserver smtp.qq.com port 465 username xxxx@qq.com password xxxxxxxxxx using tlsv1  
    set mail-format {
       from:    xxxxxxx@qq.com
       subject: monit alert --  $EVENT $SERVICE
       message: $EVENT Service $SERVICE
                     Date:        $DATE
                     Action:      $ACTION
                     Host:        $HOST
                     Description: $DESCRIPTION

                Your faithful employee,
                Monit
    }
    set alert xxxxxxx@qq.com

#### ubuntu 安装monit
1. `apt-get install monit`

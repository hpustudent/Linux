1.    `sudo apt-get update`

2.  `sudo apt-get install mysql-server`

3.  `sudo service mysql restart`出现以下提示说明启动成功：
        
        mysql stop/waiting
        
        mysql start/running, process 6042
        
4.    `mysql -uroot -p`输入密码，进入mysql命令行。

5.    授权
    
          GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
          授权所有主机可以以root身份，123456为密码登录进mysql
          flush privileges刷新权限即可
           
      撤回权限：revoke all privileges on *.* from dba@localhost;     
           
6.  设置mysql绑定地址
    
          vim /etc/mysql/my.cnf
          修改 bind-address:127.0.0.1-> bind-address:0.0.0.0
    
7. service mysql restart即可

8. 如果需要代理则需要安装 mysql-proxy,使用命令apt-get install mysql-proxy ,安装完成后使用mysql-proxy -V 测试安装是否成功,如果成功会显示版本号

* 8.1 系统默认将程序安装在 /usr/bin/mysql-proxy  
* 8.2 系统默认将管理 mysql-proxy的lua脚本放在/usr/lib/mysql-proxy/lua/admin.lua  
* 8.3 可以在 /usr/local下创建mysql-proxy目录，存放启动配置文件，编辑 mysql-proxy.conf配置文件 

      [mysql-proxy]
      pid-file = /var/run/mysql-proxy.pid
      log-file = /usr/local/mysql-proxy/mysql-proxy.log
      log-level = debug
      max-open-files = 1024
      plugins = admin,proxy

      #Proxy Configuration(代理开发机)
      proxy-address = 当前主机ip:绑定的端口

      #线上数据库地址,主数据库，可以配置读写分离
      proxy-backend-addresses = 后端数据库host:ip
      #proxy-read-only-backend-addresses =
      #proxy-lua-script =
      #proxy-skip-profiling = true

      # Admin Configuration，配置管理端
      admin-address = 127.0.0.1:管理端绑定端口
      admin-lua-script = /usr/lib/mysql-proxy/lua/admin.lua
      admin-username = admin
      admin-password = admin

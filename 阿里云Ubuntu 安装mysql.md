1.    `sudo apt-get update`

2.  `sudo apt-get install mysql-server`

3.  `sudo service mysql restart`出现以下提示说明启动成功：
        
        mysql stop/waiting
        
        mysql start/running, process 6042
        
4.    `mysql -uroot -p`输入密码，进入mysql命令行。

5.    授权

    `GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;`

`授权所有主机可以以root身份，123456为密码登录进mysql`

`flush privileges刷新权限即可`
           
6.  设置mysql绑定地址
    
    vim /etc/mysql/my.cnf
    修改 bind-address:127.0.0.1-> bind-address:0.0.0.0
7. service mysql restart即可

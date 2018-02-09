### `sudo apt-get install supervisor`命令安装supervisor服务

1. 使用`service supervisor status`测试服务状态
2. 在`/etc/supervisor/supervisord.conf`中配置服务

        ; supervisor config file
        [unix_http_server]
        file=/var/run//supervisor.sock   ; (the path to the socket file)
        chmod=0700                       ; sockef file mode (default 0700)

        [supervisord]
        logfile=/var/log/supervisor/supervisord.log ; (main log file;default $CWD/supervisord.log)
        pidfile=/var/run/supervisord.pid ; (supervisord pidfile;default supervisord.pid)
        childlogdir=/var/log/supervisor            ; ('AUTO' child log dir, default $TEMP)

        ; the below section must remain in the config file for RPC
        ; (supervisorctl/web interface) to work, additional interfaces may be
        ; added by defining them in separate rpcinterface: sections
        [rpcinterface:supervisor]
        supervisor.rpcinterface_factory = supervisor.rpcinterface:make_main_rpcinterface

        [supervisorctl]
        serverurl=unix:///var/run//supervisor.sock ; use a unix:// URL  for a unix socket

        ; The [include] section can just contain the "files" setting.  This
        ; setting can list multiple files (separated by whitespace or
        ; newlines).  It can also contain wildcards.  The filenames are
        ; interpreted as relative to this file.  Included files *cannot*
        ; include files themselves.

        [include]
        files = /etc/supervisor/conf.d/*.conf

3. 添加程序可以在supervisord.conf文件中添加，也可以在conf.d/文件夹下添加.conf文件  
      [program:test]  
      directory = /usr*****  //表示test所在的工作目录  
      command = python /home/test.py  
      priority = 1 //优先级按照优先级从高到低依次启动，数字越大，越先启动  
      autostart = true   //程序是否随着supervisor的启动而启动  
      autorestart = true // 程序停止时是否自动重启  
      stdout_logfile = /var/log/supervisord/test_server.log  
      redirect_stderr=true //重定向错误日志到标准输出上  
      user = root    
      stdout_logfile_maxbytes=20MB  ; stdout 日志文件大小，默认50MB  
      stdout_logfile_backups = 20   
      
      numprocs=3  //进程数量  
      numprocs_start=1 //编号起始  
      process_name=%(program_name)s_%(process_num)02d  //进程名字  

4. 启动supervisor服务， `sudo service supervisor start`

5. 更新配置，`sudo supervisorctl update` （/etc/supervisord.conf.d/目录下添加新的配置文件后，使用update命令，会把新服务启动，而且不会影响原来的服务）

6. 重启配置，`sudo supervisorctl reload`，重新按照conf文件启动supervisor服务，所有服务都会重新启动。修改supervisord.conf文件内容，比如添加web访问，必须使用reload重新加载配置和重启supervisor服务才可以生效。

7. 启动 `sudo supervisorctl start test`，停止 `sudo supervisorctl stop test`

8. `chkconfig |grep supervisor ` 查看supervisor是否被设置为开机启动，如果没有使用 `chkconfig supervisor on` 打开开机启动。

9. `supervisorctl status`查看所有监护的进程，如果没有则显示，is running

10. `supervisorctl reread`读取有更新的文件，不会启动新添加的程序

11. 出现输出乱码情况，在supervisord.conf 的[supervisord] 字段下添加  
        `environment=LANG=en_US.UTF-8,LC_ALL=en_US.UTF-8`
 

### centos 7 安装supervisor

    yum install epel-release
    yum install -y supervisor 
    `sudo supervisord -c /etc/supervisor/supervisord.conf`  (以下两行解决 No such file or directory: file: /usr/lib/python2.7/socket.py) 
    `sudo supervisorctl -c /etc/supervisor/supervisord.conf`  




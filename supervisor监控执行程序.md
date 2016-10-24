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
      command = python /home/test.py  
      autostart = true   
      user = root    

4. 启动supervisor服务， `sudo service supervisor start`

5. 重启或者更新配置，`sudo supervisorctl update`

6. 启动 `sudo supervisorctl start test`，停止 `sudo supervisorctl stop test`

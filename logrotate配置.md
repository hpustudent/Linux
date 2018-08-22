### 安装logroate
 yum install -y logrotate cron
 
安装后，系统会在/etc/cron.daily文件夹下创建logrotate脚本， 就会每天定时执行这个脚本，使用service crond status查看crontab的状态

如果想直接执行以下logrotate，可以使用logrotate -f /etc/logrotate.d/nginx，也可以加上-d参数调试执行，logrotate -f -d /etc/logrotate.d/nginx

### logrotate的参数

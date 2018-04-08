1. `timedatectl status`查看时间状态
2. `timedatectl set-timezone Asia/Shanghai` 设置本地时区为上海
3. `ntpdate ntp1.aliyun.com`校准系统时间为服务器时间
4. 将Linux系统时钟同步到远程NTP服务器 `timedatectl set-ntp true`

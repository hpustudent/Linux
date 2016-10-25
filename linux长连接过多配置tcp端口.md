### /etc/sysctl.conf中添加如下配置
    fs.file-max = 1048576
    net.ipv4.ip_local_port_range = 1024 65535
    net.ipv4.tcp_mem = 786432 2097152 3145728
    net.ipv4.tcp_rmem = 4096 4096 16777216
    net.ipv4.tcp_wmem = 4096 4096 16777216

    net.ipv4.tcp_tw_reuse = 1
    net.ipv4.tcp_tw_recycle = 1

### /etc/security/limits.conf中添加如下配置
    *	soft nofile 1048576
    *	hard nofile 1048576

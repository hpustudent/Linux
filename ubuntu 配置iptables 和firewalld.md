### iptables -L -n查看配置信息和端口信息

1. 要添加某个端口号，`vim /etc/iptables.up.rules `
2. 复制有80端口的哪一行到下边修改80端口为自己想要的端口
3. iptables-restore < /etc/iptables.rules命令使防火墙生效查看是否生效

### 

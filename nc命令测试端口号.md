### nc 含义为 tcp和udpconnections和listens

- v 输出verbose 信息
- u udp端口号 而非默认的tcp端口号
- z nc只扫描，并不发送任何信息

例如：nc -zv cheng_server 6379 测试服务器6379端口是否存活

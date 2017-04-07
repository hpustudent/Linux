1. 使用域名或者ip地址扫描系统
* nmap baidu.com
* nmap 111.111.111.111

2. 加参数`-v` 显示扫描细节
* nmap -v baidu.com

3. 加参数`-O` 探测操作系统
* nmap -O baidu.com

4. 加参数`-sV` 检测主机服务版本号(scan version)
* nmap -sV 192.168.5.11

5. 加参数`-p` 扫描一段端口
* nmap -p 1000-10000 192.168.5.11

6. 服务器使用防火墙阻止ICMP的ping请求，加参数`-PA`可以使用TCP ACK
* nmap -PA 192.168.5.11

7. 执行秘密扫描`-sS`(scan secret)
* nmap -sS 192.168.5.11

8. 扫描多个主机只需要以空格隔开ip地址

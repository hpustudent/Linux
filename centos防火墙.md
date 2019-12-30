### systemctl start firewalld         # 启动,
### systemctl enable firewalld        # 开机启动
### systemctl stop firewalld          # 关闭
### systemctl disable firewalld       # 取消开机启动
### systemctl unmask firewalld  # unmask


### 查询端口开放情况
firewall-cmd --zone=public --query-port=80/tcp
### 永久开启端口
firewall-cmd --zone=public --add-port=80/tcp --permanent
### 删除端口
firewall-cmd --zone=public --remove-port=80/tcp --permanent
### 查看开放端口
firewall-cmd --zone=public --list-ports
### 添加白名单到publich区域，最好直接加入可信区域(`firewall-cmd --zone=trusted --add-source=1.2.3.4 --permanent`)
firewall-cmd --zone=public --add-source=1.2.3.4 --permanent
### 查询白名单
firewall-cmd --zone=public --list-sources
### 查看所有规则
firewall-cmd --zone=public --list-all
### 检查后台连接状态
firewall-cmd --state
### 查询服务是否被允许（查询ssh服务）
firewall-cmd --zone=public --query-service=ssh
### 允许某个服务器流量通过某个区域(允许https服务器通过public区)
fierwall-cmd --zone=public --add-service=https --permanent
### 禁止某个服务的流量通过某个区域
firewall-cmd --zone=public --remove-service=https --permanent
### 将原本到某端口的数据包转发到其他端口（原本到888端口的数据包转发到192.168.10.10的22端口）
firewall-cmd --zone=public --add-forward-port=port=888:proto=tcp:toport=22:toaddr=192.168.10.10
### 富规则
firewall-cmd  --add-rich-rule='rule family=ipv4 source address=192.168.1.10 service name=ssh accept" --permanent

### 允许指定ip访问端口
firewall-cmd  --add-rich-rule='rule family=ipv4 source address=192.168.1.10 port port=5432 protocol=tcp accept" --permanent
### 查询默认zone的rich rule
firewall-cmd --list-rich-rules

### 获取活动的区域 将输出每个zone和对应的网卡
firewall-cmd --get-active-zones
 
### 根据网卡名获取zone
firewall-cmd --get-zone-of-interface=<interface>

### 将网卡添加到zone
 firewall-cmd [--zone=<zone>] --add-interface=<interface>
 
### 修改网卡所属zone
 firewall-cmd [--zone=<zone>] --change-interface=<interface>

### 从区域中删除网卡
firewall-cmd [--zone=<zone>] --remove-interface=<interface>

### 列举zone中启用的服务
 firewall-cmd [ --zone=<zone> ] --list-services
 
 ### 端口转发
 firewall-cmd --permanent --zone=<区域> --add-forward-port=port=<源端口号>:proto=<协议>:toport=<目标端口号>:toaddr=<目标IP地址>  
 firewall-cmd --add-forward-port=port=80:proto=tcp:toport=8080  将80端口的请求转发到8080端口   
 firewall-cmd --add-forward-port=proto=80:proto=tcp:toaddr=192.168.10.1 将80端口请求转发到目的地址的80端口  
 
 ### 伪装ip
firewall-cmd --query-masquerade # 检查是否允许伪装IP  
firewall-cmd --add-masquerade   # 允许防火墙伪装IP  
firewall-cmd --remove-masquerade# 禁止防火墙伪装IP  
 

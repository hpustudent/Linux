### 查询端口开放情况
firewall-cmd --zone=public --query-port=80/tcp
### 永久开启端口
firewall-cmd --zone=public --add-port=80/tcp --permanent
### 删除端口
firewall-cmd --zone=public --remove-port=80/tcp --permanent
### 查看开放端口
firewall-cmd --zone=public --list-ports
### 添加白名单
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
firewall-cmd  --add-rich-rule="rule family="ipv4" source address="192.168.1.10" service name="ssh" accept" --permanent

### 允许指定ip访问端口
firewall-cmd  --add-rich-rule="rule family="ipv4" source address="192.168.1.10" port port="5432" protocol="tcp" accept" --permanent
### 查询默认zone的rich rule
firewall-cmd --list-rich-rules

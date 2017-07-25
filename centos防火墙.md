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

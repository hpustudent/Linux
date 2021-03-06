### 查看当前规则 iptables --list (或者-L),显示出三条链的所有规则，iptables -vnL --line-number,显示所有规则和行号

### 清除已有的规则 iptables 
1. iptables -F #清空所有防火墙规则
2. iptables -X #删除用户自定义规则

### 命令选项书写规则

      iptables -t 表名 <-A/I/D/R> 规则链名 [规则号] <-i/o 网卡名> -p 协议名 <-s 源IP/源子网> 
      --sport 源端口 <-d 目标IP/目标子网> --dport 目标端口 -j 动作

      iptables [-t 要操作的表] <A/D/R/I/P/F操作的命令：增删改插策略清> [要操作的链] [规则号码] [匹配条件] [-j 匹配到以后的动作]

#### 常用表名：filter net
1. filter: 包过滤规则，用于防火墙规则
2. net:地址转换，用于网关路由器
3. 默认不指定表名则操作的为filter表

#### filter表规则链动作与规则链
1. 规则链动作
* 1.1 A append,添加规则
* 1.2 I insert,插入规则
* 1.3 D delete，删除规则
* 1.4 P policy，所有规则
* 1.5 R replace, 替换规则

2. 规则链
* 2.1 INPUT链：处理进来的数据包
* 2.2 OUTPUT链：处理出去的数据包
* 2.3 PORWARD链：处理转发的数据包

      修改某条链的规则：iptables -R INPUT 4 -p icmp -j ACCEPT
      在某个序号上添加规则：iptables -I INPUT 3 -p tcp --dport 22 -j ACCEPT

#### 匹配条件
1. 流入流出接口[-i -o]
2. 来源目的地址[-s -d]
3. 协议类型[-p]
4. 来源目的端口[--dport --sport]
5. 按照包状态匹配 [-m state --state]
* 状态有： NEW RELATED ESTABLISHED INVALID四种
* `iptables - A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT`
6. 按照包速率匹配 [-m limit --limit]
* `iptables -A FORWARD -p tcp --dport 80 -m limit --limit 50/s -j ACCEPT` 
7. 多端口匹配 [-m multiport <--sports|--dports|--ports>],必须与`-p`一块使用
* `iptables - A INPUT -p tcp -m multiport --dports 21,22,80 -j ACCEPT`
8. 按来源mac地址匹配 [-m mac --mac-source]
* `iptables -A FORWARD -m mac --mac-source xx:xx:xx:xx:xx:xx -j ACCEPT`


#### -j 动作
1. ACCEPT:接收数据包
2. DROP：丢弃数据包
3. REJECT：丢掉但是回复信息
4. LOG:记录到日志
5. SNAT:源地址转换
6. DNAT：目标地址转换
7. REDIRECT:重定向

### 常用配置
1. 清空所有规则

        iptables -F
        
2. 允许ssh端口从某个ip地址登录

        iptables -A INPUT -p tcp -s 191.111.111.111 --dport 22 -j ACCEPT

3. 允许本地回环地址

        iptables -A INPUT -i lo -j ACCEPT
        iptables -A OUTPUT -o lo -j ACCEPT
      
4. 配置白名单

        iptables -A INPUT -p all -s 192.168.1.0/24 -j ACCEPT
        iptables -A INPUT -p tcp -s 122.111.111.111 --dport 3380 -j ACCEPT
       
5. 开启80端口

        iptables -A INPUT -p tcp --dport 80 -j ACCEPT 

6. 允许外部ping
        
        iptables -A INPUT -p icmp  -j ACCEPT
        
7. 允许已经建立的连接

        iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
        
8. 其他的都屏蔽掉

        iptables -P INPUT DROP
        iptables -P FORWARD DROP
        iptables -P OUTPUT ACCEPT
        
9. iptables-save > /etc/iptables.rules 将防火墙规则保存在文件中，修改/etc/network/interfaces脚本，在网卡0后边加上`pre-up iptables-restore < /etc/iptables.rules`和`post-down iptables-save > /etc/iptables.rules`

        常用配置：
        iptables -A INPUT -i lo -j ACCEPT   #允许本地回环地址
        iptables -A INPUT -p all -m state --state RELATED,ESTABLISHED -j ACCEPT #允许已经建立的连接通过
        iptables -A INPUT -p tcp -m state --state NEW --dport 22 -j ACCEPT #开放本机22端口
        iptables -A INPUT -p tcp -m state --state NEW --dport 7001 -j ACCEPT  #开放7001端口
        iptables -A INPUT -p tcp -m state --state NEW --dport 3306 -j ACCEPT  #开放 3306 端口
        iptables -A INPUT -p icmp -j ACCEPT  #允许外部ping
        iptables -P INPUT DROP #默认策略为丢弃
        

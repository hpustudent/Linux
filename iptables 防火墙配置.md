### 查看当前规则 iptables --list (或者-L),显示出三条链的所有规则，iptables -L -n --line-number,信使所有规则和行号

### 命令选项书写规则

      iptables -t 表名 <-A/I/D/R> 规则链名 [规则号] <-i/o 网卡名> -p 协议名 <-s 源IP/源子网> 
      --sport 源端口 <-d 目标IP/目标子网> --dport 目标端口 -j 动作

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

#### 协议名，tcp udp icmp

#### -j 动作
1. ACCEPT:接收数据包
2. DROP：丢弃数据包
3. REJECT：丢掉但是回复信息
4. LOG:记录到日志
5. SNAT:源地址转换
6. DNAT：目标地址转换
7. REDIRECT:重定向

### 常用写法


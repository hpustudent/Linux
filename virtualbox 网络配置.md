### 配置NAT网络
1. 新创建的虚拟机是无法访问外网的，为了访问外网，可以配置一个NAT网络地址转换虚拟网卡
2. 在 `/etc/sysconfig/network-scripts`下创建ifcfg-eth0文件

        DEVICE=eth0 
        HWADDR=查看自动创建的硬件地址
        ONBOOT=yes //是否开机启动
        NM_CONTROLLED=yes //是否被network manager 控制
        BOOTPROTO=dhcp //是否是动态获取ip

3. reboot命令重启虚拟机，重启网络不会成功的
4. 使用`ping baidu.com` 可以看到可以访问外网了

### 配置host-only 主机网络，与主机形成一个局域网
1. 关闭虚拟机
2. 添加虚拟网卡，选择连接方式为host-only适配器
3. `ip ad`命令，即将看到新的网卡配置信息，此时ping宿主主机ip可以ping通了，通过宿主主机ping虚拟机ip也可以联通了

### 配置静态ip
1. 在`/etc/sysconfig/network-scripts`

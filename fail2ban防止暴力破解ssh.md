1. `cat /var/log/secure | awk '/Failed/{print $(NF-3)}' | sort | uniq -c | awk '{print $2" = "$1;}'` 查看登录ip

2. fail2ban是一个入侵保护的开源框架，可以根据错误自动触发不同的防御

3. 安装EPEL源`yum install -y epel-release`

4. centos默认防火墙是firewalld,所以需要安装firewalld版本的fail2ban 

`yum -y install fail2ban-firewalld fail2ban-systemd`

修改`jail.d/00-firewalld.conf`为

        [DEFAULT]
        banaction = firewallcmd-new

5. 在`/etc/fail2ban/`目录下可以看到配置文件，再此目录下新建文件`jail.local`, systemctl 启动fail2ban


        [DEFAULT]
        bantime = 86400
        findtime = 300
        maxretry = 3

        [sshd]
        enabled = true


6. 查看ssh服务监护状态`fail2ban-client status sshd`

7. ssh监护服务白名单中添加删除ip

        fail2ban-client set sshd addignoreip 1.2.3.4
        fail2ban-client set sshd delignoreip 1.2.3.4

8. fail2ban日志在`/var/log/fail2ban.log`

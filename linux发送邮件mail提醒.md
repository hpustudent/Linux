1、 安装邮件软件`yum -y install sendmail mailx`  
2、编辑`/etc/mail.rc` 在末尾加上  

    set ssl-verify=strict                                                                                      
    set from=100000@qq.com                                                                                 
    set smtp="smtps://smtp.qq.com:465"                                                                         
    set smtp-auth-user="10000@qq.com"                                                                     
    set smtp-auth-password="yourpassword"                                                                  
    set smtp-auth=login                                                                                        
    set nss-config-dir=/root/ssl  

3、在上边配置中指定证书的地方生成证书,并将证书添加到系统

    echo -n "" | openssl s_client -connect smtp.qq.com:465 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > smtp.crt
    certutil -A -n 'qq' -t "P,P,P" -d . -i ./smtp.crt
    
4、使用`systemctl start sendmail`启动sendmail服务  
5、`echo 我是内容 | mail -s 我是标题 1000@qq.com`发送测试邮件

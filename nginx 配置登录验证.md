1. `yum -y install httpd-tools`

2. `htpasswd -bc login.db name password`

3. 在nginx配置下边新增

```
auth_basic "Please input password"; #这里是验证时的提示信息 
auth_basic_user_file /usr/local/src/nginx/passwd;
```

4. `nginx -s reload`重新加载配置文件即可

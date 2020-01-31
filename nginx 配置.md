#### 配置用户名密码

1. `yum -y install httpd-tools`

2. `htpasswd -bc login.db name password`

3. 在nginx配置下边新增

```
auth_basic "Please input password"; #这里是验证时的提示信息 
auth_basic_user_file /usr/local/src/nginx/passwd;
```

4. `nginx -s reload`重新加载配置文件即可

#### 调试跳转
```
location / {
    return 200 "$host $request_uri";
}
# 发送如下请求
# curl 127.0.0.1/test
# 127.0.0.1 /test
```

#### 配置location

#### rewrite模块


1. 生成rsa密钥对
        ssh-keygen -t rsa

        这一步会提示让输入密码，这里不要输入，因为本来就是要免密码登录的
        指定密钥要保存的文件 ，会生成指纹
        The key fingerprint is:
  

2. 进入指纹生成文件的目录，可以看到指定的文件例如id_rsa,同时生成了一个公钥id_rsa_pub

3. 将公钥拷贝到目标主机上  
  1. 登录到远程主机，查看/root/.ssh目录是否存在，如果不存在则创建,想用当前远程主机的那个账户登录则在相应用户名下创建.ssh目录，使用root登录，则在root下创建。

  2. 将公钥id_rsa.pub的内容写到.ssh下的authorized_keys文件中去，如果没有这个文件，则创建一个

  3. 如果目录是刚创建的，需要改变目录的权限 chmod -R 600 ~/.ssh

  4. 好了再自己电脑上ssh命令登录就不用输入密钥了

注意：系统默认寻找私钥是在~/.ssh/id_rsa这个文件，如果是要配置多个服务器免密码登录，要这么做  
  1. 在客户端~/.ssh目录下创建config文件  
  2. 在config文件中输入  
Host .....  
IdentityFile 公钥位置  
IdentityFile 私钥位置  

ok可以登录了  

## 利用ssh-copy-id 命令


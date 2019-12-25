1、`wget -c https://github.com/goharbor/harbor/releases/download/v1.10.0/harbor-online-installer-v1.10.0.tgz` 下载在线安装脚本

2、`tar -zxvf harbor-online-installer-v1.10.0.tgz ` 解压压缩包

    harbor/prepare
    harbor/LICENSE
    harbor/install.sh
    harbor/common.sh
    harbor/harbor.yml
    
3、安装docker-compose

    curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose

4、修改docker镜像影像`vim /etc/docker/daemon.json`

    {                                                                                                          
     "registry-mirrors":[
      "https://*********.mirror.aliyuncs.com"
     ]
    }
    
5、修改harbor配置文件harbor.yml  
1）修改为`hostname`，修改为本机的外网ip    
2）修改为`port`，修改为本机对外暴露的访问端口号    
3）修改为注销掉https的设置  
4）修改为`data_volume`修改为/data/harbor 创建个空文件夹专门存放harbor相关文件  
5）修改`harbor_admin_password`的初始密码  

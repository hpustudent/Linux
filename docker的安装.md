1、运行`yum remove docker docker-client  docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine`清除掉旧版本  

2、执行`yum install -y yum-utils device-mapper-persistent-data lvm2`安装yum-config-manager  

3、执行`yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo` 添加源  

4、执行`yum install docker-ce docker-ce-cli containerd.io`安装社区版docker  ，也可以使用`$ sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io`安装指定版本的docker  

5、执行`systemctl start docker`启动docker  

6、执行`docker run hello-world`启动hello-world 测试安装是否成功 `docker version 或者docker info获取docker安装信息`

#### 使用一键安装脚本
1、`curl -sSL https://get.daocloud.io/docker | sh`     使用文档 https://get.daocloud.io/

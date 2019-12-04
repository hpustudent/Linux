1、运行`yum remove docker docker-client  docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine`清除掉旧版本  

2、执行`yum install -y yum-utils device-mapper-persistent-data lvm2`安装yum-config-manager  

3、执行`yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo` 添加源  

4、执行`yum install docker-ce docker-ce-cli containerd.io`安装社区版docker  ，也可以使用`$ sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io`安装指定版本的docker  

5、执行`systemctl start docker`启动docker  

6、执行`docker run hello-world`启动hello-world 测试安装是否成功 `docker version 或者docker info获取docker安装信息`

#### 使用一键安装脚本
1、`curl -sSL https://get.daocloud.io/docker | sh`     [使用文档](https://get.daocloud.io/)  

2、docker国内镜像，使用`vim /etc/docker/daemon.json`,输入以下内容，并重启docker服务`systemctl restart docker`生效,通过info也可以
查看到当前的源是否生效  

    {
        "registry-mirrors": [
            "https://registry.docker-cn.com"
        ]
    }

3、如果要使用阿里云镜像源可以[阿里云docker](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)  

#### image
1、docker把应用程序以及依赖添加到image文件中，通过image文件生成容器，同一个image文件，可以生成多个同时运行的容器实例

2、使用`docker image ls 或者docker image rm`查看或删除image文件,更推荐使用`docker images`    

3、使用`docker image pull library/test`表示从仓库中获取library/test的image文件，library是组名，test是文件名，docker官方提供的image文件，
都放在library中，可以不写默认的组名，简化为`docker image pull test`

4、使用`docker container run test`，将test运行在容器中，`container run`会自动抓取image文件，所以即使不写pull，也会先执行pull在run  

5、容器执行后，会自动终止，如果容器提供的是服务，则需要使用`docker container kill [containID]`手动终止容器  

6、容器一旦生成就会同时存在image文件和容器文件，而且关闭容器不会删除容器文件，只是停掉容器运行而已`docker container ls --all` 列出本机所有容器  

7、使用`docker container rm [containerID]`删除掉本地容器文件  

#### docker根据dockfile生成二进制image文件

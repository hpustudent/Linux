1、运行`yum remove docker docker-client  docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine`清除掉旧版本  

2、执行`yum install -y yum-utils device-mapper-persistent-data lvm2`安装yum-config-manager  

3、执行`yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo` 添加源  

4、执行`yum install docker-ce docker-ce-cli containerd.io`安装社区版docker  ，也可以使用`$ sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io`安装指定版本的docker  

5、执行`systemctl start docker`启动docker  

6、执行`docker run hello-world`启动hello-world 测试安装是否成功 `docker version 或者docker info获取docker安装信息`

(`docker run --name nginx -d nginx:1.12`给指定版本的程序指定名字并且直接运行程序，但是run起来的程序是在前台执行的，可以通过`-d或--detach`选项使程序启动后与控制台脱离，使程序进入后台运行, 如果想要让程序在前台运行，可以使用`docker attach [应用名或者容器id]` attach一般不用)  

7、使用`docker inspect [应用名或id]`查看应用的详情信息  

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

6、容器一旦生成就会同时存在image文件和容器文件，而且关闭容器不会删除容器文件，只是停掉容器运行而已`docker container ls -a`或者使用`doccker ps -a` 列出本机所有容器  

7、使用`docker container rm [containerID]`删除掉本地容器文件  

#### docker根据dockfile生成二进制image文件

#### 在容器中执行操作
1、使用`docker exec`命令可以让容器执行指定的命令  
2、使用`docker exec -it nginx bash`命令可以以控制台形式进入到虚拟环境中进行交互操作（i:交互式，t：终端）,如果没有bash则使用sh  

#### 容器互联
1、启动容器时，使用选项`--link 其他容器名`就可以自动将当前容器连接到对方容器的网络下，连接的ip地址不用写具体地址，而是用对方容器名代替  

2、启动容器时，使用选项`--expose 8080` 就可以将当前启动的容器暴露一个指定的端口，给对方  

3、使用`docker network ls`查看当前容器中所有的网络，启动容器时，可以使用选项`--network bridge`将当前容器加入到指定的网络中  

4、启动容器时，使用`-p`或者`--publish`对宿主机的端口和容器端口进行映射，例如`-p 8080:80`就是将本地的8080端口映射到容器的80端口  
例子：`docker run -d --name nginx -p 8000:80 axizdkr/tengine:2.2.3 `

#### 文件数据交换
1、使用选项`-v`或者`--volume`,例如`-v /usr/local/nginx.conf:/etc/nginx.conf`指定本地宿主机的配置文件或文件夹挂载到容器中的文件或文件夹下
，启动容器后，就可以在容器中看到宿主机的文件

`-v /usr/local/nginx.conf:/etc/nginx.conf:ro`只读挂载，表示容器只能读文件不能写文件

使用`-v`选项也可以只指定容器的文件或文件夹，而不关心宿主机存放文件的位置

2、区别：绑定挂载必须同时指定宿主机文件绝对路径和容器文件绝对路径  
   volume挂载只需要指定容器文件的绝对路径，不关心宿主机文件挂载的名字和路径，如果不想使用自动生成的名字，也可以使用`-v (名字):(容器挂载目录)`来
   命名数据卷
   
3、


1、运行`yum remove docker docker-client  docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine`清除掉旧版本  
2、执行`yum install -y yum-utils device-mapper-persistent-data lvm2`安装yum-config-manager  
3、执行`yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo` 添加源

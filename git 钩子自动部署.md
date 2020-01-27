#### 远程服务器在每次用 Git 推送修改时进行部署

1. 在要部署的服务器上创建.gitrepos文件夹
```
mkdir repo1.git
cd repo1.git
git --bare init #初始化空项目
vim hooks/post-receive
chmod +x hooks/post-receive
```

2. 添加代码到post-receive中
```
#!/bin/sh

GIT_REPO=/root/.gitrepos/repo1.git
PUBLIC_WWW=/data/book/repo1

rm -rf $PUBLIC_WWW  #清除老文件夹
git clone $GIT_REPO $PUBLIC_WWW
cd $PUBLIC_WWW
gitbook build  >> /root/repo1.log #将执行日志存放到本地文件中
exit
```

注意：由于在git中执行命令的环境变量和系统环境变量不一样，需要执行`ln -s /root/.nvm/versions/node/v10.16.3/bin/* /usr/local/bin`下才可以保证gitbook命令和依赖的node命令正常执行

3. 在本机配置远程仓库
`git remote add deploy deployer@myserver.com:/root/.gitrepos/repo1.git`

4. 本地代码修改好后，使用`git push deploy master`提交，即可自动部署

## 删除git仓库中的文件或者文件夹
### git rm --cached .DS_Store 
### git add .
### git commit -m '删除DS_Store'
### git push


rm --cached 是删除文件，rm -r --cached .idea 是删除文件夹

## 拉取指定文件
1. mkdir server
2. 进入文件夹 执行git init
3. git remote add 远程仓库名 http://用户名:密码@ipd地址/路径.git
4. git fetch 远程仓库名 分支1(远程分支):分支1(本地分支)(执行这个命令会拉取服务器最新的修改，如果没有修改可以不执行)
5. git checkout 分支1 -- bin 检出merge分支的bin文件夹

示例：

mkdir test  
cd test  
git init  
git remote add rep http://root:123456@192.168.1.1/user/first.git  
git fetch rep dev:dev  
git checkout dev -- bin  


## 查看当前分支
git branch

## 检出指定版本（使用指定版本的hash值替代即可）
git checkout 6609522fccdcac12ee86cfe3d3fd09226f1708fd -- bin/dev/

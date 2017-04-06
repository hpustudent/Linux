1、which 文件查找，可以找一个命令所在的目录

2、find 可以查找任何文件所在路径  
find 某个目录 -name 关键字或者带通配符的关键字  
find 某个目录 -iname 不区分大小写查找  
find 某个目录 -size [+-=]文件大小  
find 某个目录 -user tempuser  
            
find 某个目录 ***** [+-=]时间范围  (+表示之外，-表示之内)
-amin 访问时间 access  -atime 单位为天
-cmin 属性被修改 change  -ctime 单位为天
-mmin 内容被修改 modify -mtime 单位为天
如 find /root -mmin -120 查找两小时内被修改过的文件     
                        
find 查找连接选项 -a (and) -o(or)  
find 根据文件类型查找 -type f(文件) d(目录) l(软连接)  
find查找结果操作 -exec  
如 find /root -name 111 -exec ls -l {} \;  

*匹配任意字符  
？匹配单个字符  
使用方法：find /root -name 111*  
find / -size +204800   

3、whereis 查找系统命令，出现的结果中会包含man手册所在的路径

4、grep 可以在文件内容中查找结果  
使用方法 grep 关键字 文件名  
grep -i 关键字匹配正则 文件名 可以不区分大小写  
grep -v 关键字匹配正则 文件名 排除包含 v表示反向搜索  
例如：grep -i ABC 1.txt 查找在1.txt中包含ABC切不区分大小写  
grep -v ^# 1.txt 排除在1.txt中以#开头的内容  

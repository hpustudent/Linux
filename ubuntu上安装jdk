1、将需要的文件下载到本地

2、ssh root@11.22.33.44 远程登录到服务器

3、scp命令传送到linux即可

scp命令第一个参数为源地址，第二个参数为目标主机地址

 在macbook上另开一个terminal，输入命令scp /Users/***/***/jdk-8u101-linux-x64.tar.gz root@22.33.44.55:/usr/java 
 ok，等待上传即可

4、tar -zxvf ***.tar.gz 解压缩文件

5、打开 /etc/profile 
在文件末尾添加

export JAVA_HOME=
export CLASSPATH=.:$JAVA_HOME/lib.tools.jar
export PATH=$PATH:$JAVA_HOME/bin

6、source /etc/profile 环境变量生效

7、java -version验证安装是否成功

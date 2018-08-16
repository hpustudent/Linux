## 远程调试tomcat
1. 在tomcat启动脚本下边，找到setenv.sh，设置变量JPDA_ADDRESS="0.0.0.0:8000"，必须绑定一个ip和端口
2. 在idea点击Edit configuration, 点击左边+，找到Remote,将上边服务器端口写上去即可
3. 启动tomcat时候，使用`catalina.sh jpda start `必须加上jpda参数，就可以远程调试了

## 防止tomcat启动两次
缘由：写了一个listener监听容器启动，发现调了两次contextInitialized，导致里边的行为执行了两次而出错

解决：
1. 引起这种问题的原因是设置Host虚拟主机目录和Context的docBase目录重复，造成加载了两次。
2. 在/data目录下建立webapp目录，将war包放在这个文件夹下边,设置docBase为/data/webapp/目录名

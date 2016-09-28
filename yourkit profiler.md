#yourkit profiler使用
 1.  在网盘下载yourkit pfofiler windows版本[百度网盘](https://pan.baidu.com)

 2. 在linux服务器上，wget命令+yourkit地址下载linux版本[yourkit linux](https://www.yourkit.com/download/yjp-2015-build-15088-linux.tar.bz2)

 3. tar xfg **.tar.bz2 解压文件,解压后会有解压包在当前路径下

 4. `java -agentpath:/root/yjp-2015-build-15088/bin/linux-x86-64/libyjpagent.so -jar TestJava.jar` 在正常java -jar **.jar 开始加上-agentpath:****/libyjpagent.so
 即可，提示 [YourKit Java Profiler 2015 build 15088] Log file: /root/.yjp/log/TestJava-13428.log log文件生成就说明代理启动成功了
 
 5. 在windows客户端，点击connect to remote application... 输入ip地址，会自动扫描端口进行检测

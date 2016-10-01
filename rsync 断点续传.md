#rsync断点续传常用参数
-P 打开断点

--rsh 传输方式一般为ssh

本地文件地址 服务器文件地址

    rsync -P --rsh=ssh MySQL-server-5.5.34-1.linux2.6.x86_64.rpm root@****:/root


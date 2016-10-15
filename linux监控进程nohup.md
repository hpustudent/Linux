nohup java -jar test.jar >nohup.log 2>&1 &  
进程在用户退出登录仍继续运行  
后台运行程序：java -jar test.jar 将标准输出输出到nohup.log 将标准错误也输出到标准输出的  
如果不想生成log，可以>/dev/null 输出到系统这个文件中的任何东西都不会保留  

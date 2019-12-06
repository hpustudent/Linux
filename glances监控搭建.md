1、初始化环境`curl -L https://bit.ly/glances | /bin/bash`  

2、`pip install glances`安装glances  

3、`vim /etc/glances/glances.conf`配置服务端口  

    [restful]                                                                                                     
    host=127.0.0.1                                                                                                
    port=6789                                                                                                     
    protocol=http                                                                                                 
    path=/ 

4、使用`glances --export restful`启动上报

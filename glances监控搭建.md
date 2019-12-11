1、初始化环境`curl -L https://bit.ly/glances | /bin/bash`  

遇到错误可以使用`pip install --upgrade setuptools && python -m pip install --upgrade pip  pip install cassandra-driver --install-option="--no-cython"`升级环境  
无法拉取shell脚本使用`git clone https://github.com/nicolargo/glancesautoinstall.git`下载到本地  
  
2、`pip install glances`安装glances  

3、`vim /etc/glances/glances.conf`配置服务端口  

    [restful]                                                                                                     
    host=127.0.0.1                                                                                                
    port=6789                                                                                                     
    protocol=http                                                                                                 
    path=/ 

4、使用`glances --export restful`启动上报

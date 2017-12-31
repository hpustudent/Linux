### `curl  https://get.acme.sh | sh`
### `acme.sh  --issue  -d mydomain.com -d www.mydomain.com  --webroot  /home/wwwroot/mydomain.com/`

### 对于nginx来说 (注意：如果路径不存在需要手动创建路径，命令才可以执行成功)使用命令 

    acme.sh --installcert -d mydomin.com
    --key-file /etc/nginx/ssl/simixinshi.com.key 
    --fullchain-file /etc/nginx/ssl/fullchain.cer --reloadcmd "service nginx force-reload"

### `service nginx force-reload`重启nginx，使用nginx reload是无效的

### 修改nginx 配置

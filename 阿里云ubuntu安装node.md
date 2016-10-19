- 执行命令`wget -c https://nodejs.org/download/release/v4.6.0/node-v4.6.0-linux-x64.tar.gz` 断点续传下载node二进制包
- 执行命令 `tar -zxvf 包名` 解压
- 进入解压包 执行 `./bin/node -v` 和 `./bin/npm -v`都正常显示版本信息就安装成功
- 路径配置到环境变量
- `npm install -g cnpm --registry=https://registry.npm.taobao.org` 安装全局cnpm 使用cnpm使用taobao镜像替代nodejs.org里边的库

- 防止node退出，需要daemon进程监控，可以使用 `npm install -g forever`，然后使用 `forever start ./bin/www` 启动，好了，这个node程序就不会退出了

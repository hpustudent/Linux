### 1. 下载iterms2
### 2. `curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh` 安装oh-my-zsh
### 3. 安装powerline 
   * 3.1 安装python包管理工具 `sudo easy_install pip`
   * 3.2 `pip install powerline-status` 安装powerline,注意，mac电脑可能报错，此时使用 `pip install --user powerline-status`   
   将包仅仅安装在当前用户下。
### 4. 下载与安装字体库
   * 4.1 `git clone https://github.com/powerline/fonts.git` 将字体从git上下载到本地
   * 4.2 进入文件中，执行`./install.sh` 脚本，完成字体安装
   * 4.3 安装后提示所有字体都安装在了用户根目录下，Library/Fonts目录中
   * 4.4 安装完字体后，选择preferences -> profiles -> Text -> change font(注意要设置两个地方Default和Hotkey window) 修改字体为下载的字体中的一种
### 5. 安装配色方案
   * 5.1 下载 `https://github.com/altercation/solarized`，进入目录中的iterm2-colors-solarized，双击，  
   Solarized Dark.itermcolors和Solarized Light.itermcolors,导入配色方案到iterm2
   * 5.2 选择preferences -> profiles ->colors -> load presets 选择安装的配色主题
### 6. 使用agnoster主题
   * 6.1 下载`https://github.com/fcamblor/oh-my-zsh-agnoster-fcamblor` ,执行install文件，会自动安装到`.oh-my-zsh/themes`目录下
   * 6.2 `vim ~/.zshrc`编辑zshrc文件，将ZSH_THEME=的主题修改为agnoster
### 7. 使用chsh -s /bin/zsh 即可 切换为zsh操作 

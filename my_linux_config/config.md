# linux 常用安装配置脚本

- 一键换源 `curl -sSL https://linuxmirrors.cn/main.sh | sudo bash` `bash <(curl -sSL https://linuxmirrors.cn/main.sh)`

- 安装常用软件 `sudo apt install -y git htop btop zsh gcc g++ cmake make python3 vim vim-airline curl unzip`

- 安装ohmyzsh `sh -c "$(curl -fsSL https://gitee.com/Devkings/oh_my_zsh_install/raw/master/install.sh)"`

- 安装zsh插件
  - 命令提示插件 `git clone https://gitee.com/imirror/zsh-autosuggestions.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`
  - 语法高亮插件 `git clone https://gitee.com/imirror/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting`
 
- 安装Qt5开发环境
  - `sudo apt install qtbase5-dev qttools5-dev-tools qttools5-dev qtcreator qtbase5-examples qtbase5-doc qtbase5-doc-dev qtbase5-doc-html `

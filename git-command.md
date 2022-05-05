# git基本操作命令
## 用户配置
```
git config --global user.name "Your Name"          // 添加用户名
git config --global user.email "email@example.com" // 添加用户邮箱
git config --list                                  // 列出git中的用户信息
git config -e --global                             // 打开git配置信息
```
## 远程仓库配置
```
ssh-keygen -t rsa -C "youremail@example.com"       // 创建ssh密钥
git remote add [shortname] [url]                   //将本地仓库与远程仓库关联
git remote -rm <file>                              // 删除远程仓库文件 
git fetch                                          // 从远程仓库拉取代码库
git clone                                          // 将远程仓库下载至本地
git push -u origin master                          // 将本地仓库推送至远程库
git pull                                           // 下载远程库并合并

```
## 基本操作
```
git init                                          // 初始化用户目录，建立git文件仓库
git add <file1> <file2> ...                       // 把编写的文件添加到暂存区
git commit -m "description of your operation"     // 把暂存区的文件提交到仓库
git rm                                            // 删除本地库中的文件
git mv                                            // 移动本地库中的文件
git reset                                         // 回退至某个代码版本
git tag [-a]
git tag -a <tagname> -m "description of message"
```
## 分支管理
```
git branch <branchname>                           // 新建分支
git checkout [-b][-d] <branchname>                // 切换分支
git merge                                         // 合并分支
```
## 日志记录
```
git status                                       // 查看仓库当前的状态，显示有变更的文件
git diff                                         // 比较文件的不同，即暂存区和工作区的差异
git log                                          // 查看提交日志
    [--oneline]
    [--graph]
    [--reverse]
    [--author]
    [--since]
    [--before]
    [--until]
    [--after]                                       
git reflog                                      // 查看简化的提交日志
git blame <file>                                // 以列表的形式查看历史修改记录
```
# git基本操作命令
## 用户配置
- `git config --global user.name "Your Name"`           <p>添加用户名</p>
- `git config --global user.email "email@example.com"`  <p>添加用户邮箱</p>
- `git config --list`                                   <p>列出git中的用户信息</p>
- `git config -e --global`                              <p>打开git配置信息</p>

## 远程仓库配置
- `ssh-keygen -t rsa -C "youremail@example.com"`        <p>创建ssh密钥</p>
- `git remote add [shortname] [url]`                    <p>将本地仓库与远程仓库关联</p>
- `git remote -rm <file>`                               <p>删除远程仓库文件</p> 
- `git fetch`                                           <p>从远程仓库拉取代码库</p>
- `git clone`                                           <p>将远程仓库下载至本地</p>
- `git push -u origin master`                           <p>将本地仓库推送至远程库</p>
- `git pull`                                            <p>下载远程库并合并</p>

## 基本操作
- `git init`                                            <p>初始化用户目录，建立git文件仓库</p>
- `git add <file1> <file2> ...`                         <p>把编写的文件添加到暂存区</p>
- `git commit -m "description of your operation"`       <p>把暂存区的文件提交到仓库</p>
- `git rm`                                              <p>删除本地库中的文件</p>
- `git mv`                                              <p>移动本地库中的文件</p>
- `git reset`                                           <p>回退至某个代码版本</p>
- `git tag [-a]`
- `git tag -a <tagname> -m "description of message"`

## 分支管理
-`git branch <branchname>`                               <p>新建分支</p>
-`git checkout [-b][-d] <branchname>`                    <p>切换分支</p>
-`git merge`                                             <p>合并分支</p>

## 日志记录
- `git status`                                           <p>查看仓库当前的状态，显示有变更的文件</p>
- `git diff`                                             <p>比较文件的不同，即暂存区和工作区的差异</p>
- `git log [--oneline] [--graph] [--reverse] [--author]
           [--since] [--before] [--until] [--after]`     <p>查看提交日志</p>
- `git reflog`                                           <p>查看简化的提交日志</p>
- `git blame <file>`                                     <p>以列表的形式查看历史修改记录</p>
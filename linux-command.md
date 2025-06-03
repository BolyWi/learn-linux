# linux基础操作命令
## 系统操作
```c
systemctl [option] 
init 6 / reboot  //重启  
init 0 / halt / shutdown / poweroff  //关机
shutdown -h [time] // 指定何时关机
man [-k]        //显示手册帮助文档 
                //man page说明后面的数字中，1代表一般帐号可用指令，8代表系统管理员常用指令，5 代表系统配置文件格式；
info            //显示命令信息
                //info page可将一份说明文档拆成多个节点（node）显示，并具有类似超链接的功能，增加易读性；
clear            //清屏  
ip addr          //查看服务器ip地址  
date			 //查看时间
cal              //查看日历
cal [month] [year] //显示某年某月的日历
cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime //设置时区为中国上海  
date -s "yyyy-mm-dd hh:mi:ss" //设置时间 
```

## 权限操作
```c
chgrp          //改变文件所属群组
chown         //改变文件所有者
chmod         //改变文件权限
```

## 文件操作
```c
pwd								//显示当前工作目录  
cd 目录名					   //改变当前工作目录  
ls [-lt -al] 目录或文件名          //列出目录和文件信息
    -al         //列出所有文件属性
	-l          //列出目录和文件名详细的信息  
	-t          //列出目录和文件名详细的信息按时间降序排序  
正则表达式  
	*           //匹配任意数量的字符  
	?           //匹配一个字符  
mkdir 目录名  
rm [-rf] 目录或文件列表  // 删除文件或文件夹
	-r  
	-f  
	-rf  
mv 旧目录或文件名 新目录或文件名  // 移动或重命名文件或文件夹
cp [-r] 旧目录或文件名 新目录或文件名  // 拷贝文件或文件夹
which [-a] command                      // 
type
cat 文件名   											// 从第一行查看文本文件内容
tac 文件名                                              // 从最后一行查看文本文件内容
more 文件名    											// 分页查看文本文件内容
less 文件名                                             // 查看文本文件内容，可上下翻页
head 文件名                                             // 显示文本的前面几行，并实时刷新
tail -f 文件名 											// 显示文本的最后几行，并实时刷新
od 文件名                                               // 将文本以而进制形式显示
wc 文件名  												// 统计文本的行数、列数
grep “内容” 文件名 										// 搜索文件中的内容
find 目录名 -name 文件名 -print 						// 查找目录中的文件并打印
find [PATH] [option] [action]
		-mtime n //在n天之前的一天之内被更改过的文件
		-mtime +n //列出在n天之前被更改过的文件和文件名
		-mtime -n //在n天之内更改过的文件
		-mtime file //列出比file更新的文件名
		-uid n //
		-gid n
		-user name 
		-group name
		-nouser
		-nogroup
		-name filename
		-size [+-]SIZE //c:byte,k:1024bytes
		-type TYPE //f:正规文件，d:目录文件，l：链接文件，s:socket, p:FIFO
		-perm mode
		-perm -mode
		-perm /mode
		-exec command
		-print
touch 文件名                                           // 修改文件时间、创建新文件
file 文件名                                             // 查看文件类型
```

## 查找操作
```c
locate                                  // 利用数据库来搜寻文件名
whereis                                 // 由一些特定的目录中寻找文件文件名
```

## 解压
```c
tar zcvf [压缩包文件名] [目录或文件列表]  
tar zxcf [压缩包文件名]  
```
## 网络操作  
```c
ping -c 包的个数 ip地址或域名
```
## 文件隐藏属性设置
```c
chgrp
chown
chmod
chattr                                                  // 设置文件其他属性
lsattr                                                  // 查看文件其他属性
umask [-S] [number]                                     // 文件默认权限设置
```

## 进程操作  
```c
Ctrl + z    //暂停当前进程
Ctrl + c    //结束当前进程
fg %1       //调回前景运行程序 
bg %2       //将背景环境程序运行
ps          //显示当前任务状态
```

## 用户群组操作  
```c
groupadd 用户组                							//添加用户组
groupdel 用户组                 							// 删除用户组
useradd -n 用户名 -g 组名 -d 用户的主目录					  // 添加用户
userdel 用户名                            					 //  删除用户
passwd [用户名]                           					 // 修改密码
su - root                                  				    // 切换用户
chown [-R] 用户名:组名 目录或文件名列表   	                  // 更改文件的用户名或用户组
df [-h][-T]                                                  // 查看磁盘信息
```
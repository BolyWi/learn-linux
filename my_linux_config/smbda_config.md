sudo apt-get install samba samba-common-bin
# 安装

sudo nano /etc/samba/smb.conf
#修改配置文件

# 在smb.conf文件末尾加入下边两段

[myshare]                       # 显示名称
comment = my share directory    # 共享说明
path = /home/pi                 # 共享目录，可自行修改
browseable = yes                # 可读权限
writeable = yes                 # 写入权限
guest ok = yes                  # 可写可不写

[portable]                      # 移动硬盘
comment = portable disk        
path = /media/pi                # 移动硬盘目录，接几个都会显示在这里
browseable = yes                
writeable = yes                 
guest ok = yes

# 保存（ctrl+o）退出（ctrl+x）

sudo smbpasswd -a pi
# 默认用户pi，设置密码

sudo smbpasswd -e pi
# 激活用户

sudo service smbd restart
# 重启服务

sudo /etc/init.d/samba start
# 如果没有开启，可以手动开启，如果还连不上就重启树莓派吧

sudo nano /etc/rc.local
# 如需自动启动，可将上一行命令（sudo /etc/init.d/samba start—）加到exit 0 之前

Q：IOS设备文件只读权限问题  
A：添加如下配置到`etc/samba/smb.conf`  
 `[global]`
 `vfs objects = streams_xattr`

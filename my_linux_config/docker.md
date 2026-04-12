# Learn Docker

## SetUp Docker
-  `bash <(wget -qO- https://xuanyuan.cloud/docker.sh)` 一键换源指令
```json
{
  "registry-mirrors": [
    "https://docker.1ms.run"
  ]
}
```
-  `docker run -it --entrypoint /bin/bash ollama/ollama` 指定bash入口点

# Docker 常用命令速查表

## 📋 基础信息类

```bash
docker version          # 查看版本信息
docker info            # 查看系统信息
docker --help          # 查看帮助
```
🖼️ 镜像管理
```bash
docker images          # 列出所有镜像
docker search nginx    # 搜索镜像
docker pull nginx:latest    # 拉取镜像
docker push username/nginx  # 推送镜像
docker rmi nginx       # 删除镜像
docker rmi -f nginx    # 强制删除
docker build -t myapp .     # 构建镜像
docker tag nginx mynginx:1.0  # 打标签
docker save -o nginx.tar nginx  # 导出镜像
docker load -i nginx.tar      # 导入镜像
```
📦 容器管理
基础操作
```bash
docker ps              # 查看运行中的容器
docker ps -a           # 查看所有容器
docker start mynginx   # 启动容器
docker stop mynginx    # 停止容器
docker restart mynginx # 重启容器
docker rm mynginx      # 删除容器
docker rm -f mynginx   # 强制删除
docker rm $(docker ps -aq)  # 删除所有容器
```
运行容器
```bash
docker run nginx       # 创建并启动容器
docker run -d nginx    # 后台运行
docker run -it ubuntu /bin/bash  # 交互式运行
docker run -p 80:80 nginx  # 端口映射
docker run -v /data:/data nginx  # 挂载卷
docker run --name mynginx nginx  # 指定名称
```
容器交互
```bash
docker exec -it mynginx /bin/bash  # 进入容器
docker logs mynginx    # 查看日志
docker logs -f mynginx # 实时查看日志
docker top mynginx     # 查看容器进程
docker inspect mynginx # 查看详细信息
docker stats           # 查看资源占用
docker cp file.txt mynginx:/tmp/  # 复制文件到容器
docker cp mynginx:/tmp/file.txt .  # 从容器复制文件
```
🌐 网络管理
```bash
docker network ls      # 列出网络
docker network create mynet  # 创建网络
docker network inspect mynet # 查看网络
docker network rm mynet     # 删除网络
docker network connect mynet mynginx  # 连接容器到网络
docker network disconnect mynet mynginx  # 断开容器网络
docker run --net=mynet nginx  # 指定网络运行容器
```
💾 数据卷管理
```bash
docker volume ls       # 列出数据卷
docker volume create mydata  # 创建数据卷
docker volume inspect mydata # 查看数据卷
docker volume rm mydata     # 删除数据卷
docker volume prune   # 删除未使用的数据卷
```
🧹 清理命令
```bash
docker system prune    # 清理未使用的数据
docker system prune -a # 清理所有未使用的数据
docker container prune # 清理停止的容器
docker image prune     # 清理未使用的镜像
docker volume prune    # 清理未使用的卷
docker network prune   # 清理未使用的网络
```
🔧 常用组合命令
```bash
# 停止所有容器
docker stop $(docker ps -q)

# 删除所有停止的容器
docker container prune

# 删除所有镜像
docker rmi $(docker images -q)

# 删除所有未打标签的镜像
docker rmi $(docker images -f "dangling=true" -q)

# 进入容器（使用容器名或ID）
docker exec -it $(docker ps -q) /bin/bash
```
🐳 Docker Compose 常用命令
```bash
docker-compose up      # 启动服务
docker-compose up -d   # 后台启动
docker-compose down    # 停止并删除
docker-compose ps      # 查看状态
docker-compose logs    # 查看日志
docker-compose logs -f # 实时查看日志
docker-compose exec web bash  # 进入服务
docker-compose restart # 重启服务
docker-compose stop    # 停止服务
docker-compose start   # 启动服务
docker-compose build   # 构建或重建服务
docker-compose pull    # 拉取服务镜像
```
📝 实用示例
Ollama 容器运行示例
```bash
# 直接运行（前台）
docker run -it ollama/ollama:latest

# 后台运行
docker run -d --name ollama -p 11434:11434 ollama/ollama:latest

# 带挂载卷运行（保存模型）
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:latest

# 保存日志到文件
docker run -it ollama/ollama:latest > /tmp/ollama.log
```
Nginx Web 服务器示例
```bash
# 运行 Nginx 并映射端口
docker run -d --name web -p 80:80 -v /var/www:/usr/share/nginx/html nginx

# 查看访问日志
docker logs -f web
```
MySQL 数据库示例
```bash
# 运行 MySQL
docker run -d --name mysql \
  -e MYSQL_ROOT_PASSWORD=123456 \
  -p 3306:3306 \
  -v mysql_data:/var/lib/mysql \
  mysql:8.0
💡 常用参数说明
参数	说明
-d	后台运行容器
-it	交互式运行（分配终端）
-p	端口映射 主机端口:容器端口
-v	挂载卷 主机目录:容器目录
--name	指定容器名称
--rm	容器退出后自动删除
-e	设置环境变量
--net	指定网络
--restart	重启策略（always/on-failure）
```
📚 常用重启策略
```bash
docker run --restart=always nginx     # 总是重启
docker run --restart=on-failure:3 nginx  # 失败时最多重启3次
```

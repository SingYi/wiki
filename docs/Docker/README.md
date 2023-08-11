# Docker

## 安装(社区版本 docker-ce)
 1. 首先安装 yum 工具

 `yum install -y yum-utils`

 2. 添加镜像

 ```yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo```

 ```yum-config-manager --add-repo http://mirrors.cloud.tencent.com/docker-ce/linux/centos/docker-ce.repo```

 3. 安装 docker-ce

 `yum install -y docker-ce docker-ce-cli containerd.io`

 4. 启动 docker 服务
 
 `systemctl start docker`


## 常用指令
### -t
在新容器内指定一个伪终端或者终端

### -i
允许你对容器内的标准输入(STDIN)进行操作

### -v
将宿主机目录挂载到容器目录，必须为绝对路径，冒号后为容器挂载的路径

`-v /var/run/docker.sock:/var/run/docker.sock`

### --name
命名容器

`--name [name]`

### -p
容器内部端口绑定到指定主机端口

### -P
容器内部端口随机映射到主机高端口

## 可视化工具
portainer.io
 1. 拉取镜像
  
  `docker pull docker.io/portainer/portainer-ce:latest`

 2. 构建容器 
  
  ```docker run -d -p 8000:8000 -p 9000:9000 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest```

## 将容器打成镜像
 - -a, --author: 镜像的作者。
 - -c, --change: 使用 Dockerfile 来创建镜像。
 - -m, --message: 镜像的说明。
 - -p, --pause: 在 commit 时，是否暂停容器。

示例:
`docker commit -a "sans" -m "Added new feature" [容器id] [镜像名称]:[tag]`

## 将打包好的镜像推送到远端仓库
示例:
`docker push [镜像名称]:[tag]`

## 通过 Dockerfile 打包镜像
# SteamCMD 的安装

## 官网
[https://developer.valvesoftware.com/wiki/SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD)

## 尝试采用 docker 安装
> 官网推荐操作

```docker run -it --name=steamcmd -v /root/app:/home/steam/steamcmd/app --privileged=true cm2network/steamcmd bash```

### 1. 先拉取 docker 镜像
`docker pull cm2network/steamcmd:latest`

### 2. 创建容器
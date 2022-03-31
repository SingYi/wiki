# 求生之路2服务器搭建

## 步骤一：[SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD)
求生之路2的服务器搭建需要依赖使用 `SteamCMD` ，所以，首先需要安装 SteamCMD。SteamCMD 官方文档[https://developer.valvesoftware.com/wiki/SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD)

 - windows:直接点击下载 [https://steamcdn-a.akamaihd.net/client/installer/steamcmd.zip](https://steamcdn-a.akamaihd.net/client/installer/steamcmd.zip)
 - linux:官方文档中说不需要使用 root 权限，推荐创建一个用户，然后进行相关操作
    - Ubuntu/Debian:
    ```
    sudo apt install steamcmd
    ```
    - RedHat/CentOS：
    ```
    yum install steamcmd
    ```
 - docker:
  ```
  docker run -it --name=steamcmd cm2network/steamcmd bash
  ```

## 步骤二：登录
安装 steam 上大部分游戏服务端，都需要登录
```
login <username>
```
匿名登录
```
login anonymous
```

登录之后配置安装路径
```
force_install_dir <path>
```

## 步骤三：安装服务端
安装和更新服务端使用的都是 `app_update` 指令
```shell
app_update <app_id> [-beta <betaname>] [-betapassword <password>] [validate]
```
例如：
```shell
app_update 740 validate
```
求生之路2服务器安装指令
```shell
app_update 222860 validate
```

## 步骤四：启动服务


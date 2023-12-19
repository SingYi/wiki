# 聊天模块 - 服务器端
服务器端采用 ejabberd 开源库。

官网: [https://docs.ejabberd.im/get-started/](https://docs.ejabberd.im/get-started/)

Github : [https://github.com/processone/ejabberd](https://github.com/processone/ejabberd)

## 端口说明
1. 5222（c2s）：客户端到服务器的通信端口，用于用户登录、发送和接收消息等。
2. 5269（s2s）：服务器到服务器的通信端口，用于不同 ejabberd 服务器之间的通信和消息路由。
3. 5280（http）：HTTP 管理接口端口，用于通过 Web 界面管理 ejabberd 服务器。
4. 5281（https）：HTTPS 管理接口端口，用于通过加密的方式进行 Web 界面管理。
5. 1883（mqtt）：MQTT 协议端口，用于支持 MQTT 协议的消息通信。
6. 4369（epmd）：Erlang Port Mapper Daemon 端口，用于 Erlang 节点之间的通信和发现。

## 配置文件示例
```
hosts:
  - "example.com"

listen:
  - 
    port: 5222
    module: ejabberd_c2s
    certfile: "/path/to/cert.pem"
    starttls: true
    protocol_options: 'TLS_OPTIONS'
  - 
    port: 5269
    module: ejabberd_s2s_in
  - 
    port: 5280
    module: ejabberd_http
    request_handlers:
      "/websocket": ejabberd_http_ws
    web_admin: true
    http_bind: true
    tls: true
    certfile: "/path/to/cert.pem"

acl:
  admin:
    user:
      - "admin_user@example.com"

access:
  c2s_shaper:
    none: normal
  s2s_shaper: fast

auth_method: sql
sql_type: mysql
sql_server: "localhost"
sql_database: "ejabberd"
sql_username: "your_username"
sql_password: "your_password"

extauth_program: "/path/to/your/extauth_program"

modules:
  mod_filter:
    access: all
  mod_ping: {}
  mod_adhoc: {}

certfiles:
  - "/path/to/cert.pem"

c2s_require_encryption: true
s2s_require_encryption: true
```

# 简单配置
官方推荐安装 : [https://docs.ejabberd.im/admin/installation/](https://docs.ejabberd.im/admin/installation/)

## linux 安装
[https://docs.ejabberd.im/admin/installation/#linux-run-installer](https://docs.ejabberd.im/admin/installation/#linux-run-installer)

 1. 下载对应的 ejabberd 版本。
 2. 添加执行权限。
 3. 运行执行文件。
 4. 生成管理员账号。
 5. 配置 config.yml 文件。
 6. 重启服务。

## 配置数据库


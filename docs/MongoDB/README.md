# MongoDB
使用 Docker 安装 MongoDB。

## 步骤一:搜索 image
docker search mongo

## 步骤二:配置 mongod.conf
设置路径 /etc/mongod.conf
```
# 数据库存储路径
dbpath=/var/lib/mongodb

# 日志文件路径
logpath=/var/log/mongodb/mongod.log

# 监听的端口
port=27017

# 允许所有的 IP 地址连接
bind_ip=0.0.0.0

# 关闭日志记录
journal=false

# 启用身份验证
auth=true
```

## 步骤二:启动容器
```
docker run --name <your db name> \
  -p <hostport>:27017 \
  -v <config file address>:/etc/mongod.conf \
  -v <dbpath>:/var/lib/mongodb \
  -v <logpath>:/var/log/mongodb/mongod.log \
  -d \
  mongo \
  --auth
```

```
docker run --name mongo \
  -p 27017:27017 \
  -v /etc/mongod.conf:/etc/mongod.conf \
  -v /root/db:/var/lib/mongodb \
  -d \
  mongo \
  --auth
```

 1. 容器名；
 2. 云服务器与容器内部的端口映射；
 3. 配置文件映射；
 4. 数据存储路径映射；
 5. 日志路径映射；
 6. 持久化后台运行；
 7. 镜像名称；
 8. 需要身份验证；

## 创建身份信息
 1. 进入容器`docker exec -it <your db name> mongosh`
 2. 创建管理员账户
 ```
 use admin
db.createUser({user: "<username>", pwd: "<password>", roles: [{role: "root", db: "admin"}]})
 ```
 3. 验证管理员账户
 `mongo -u <admin> -p <password> --authenticationDatabase admin`

 ## 安装 mongo-express
 ```
 docker run -itd --name mongo-express --network=host --env ME_CONFIG_MONGODB_SERVER='10.0.42.211' --env ME_CONFIG_MONGODB_ADMINUSERNAME='mongoadmin' --env ME_CONFIG_MONGODB_ADMINPASSWORD='mongoadmin' --env ME_CONFIG_BASICAUTH_USERNAME='mongoadmin' --env ME_CONFIG_BASICAUTH_PASSWORD='mongoadmin' mongo-express
 ```
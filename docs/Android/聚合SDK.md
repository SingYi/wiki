# 聚合 SDK
## 打包流程
### SDK 预处理
#### 一、SDK 资源合并
1. 合并 res 目录下的资源
   - layout : 布局文件
   - anim : 动画文件
   - drawable/mipmap : 图片文件
   - color : 自定义颜色文件
   - menu : 菜单定义文件
   - xml : 配置文件
   - raw : 不进行压缩的文件
   - values : 字符串、主题样式、颜色、属性、尺寸等配置文件
    ```
    - 合并 res 目录文件的时候，可能会出现文件名冲突的情况，这里在开发自研 SDK 的时候，需要尽量避免跟第三方 SDK 的文件名出现冲突，可以统一增加前缀处理。
    - 需要注意 value 目录下的 xml 文件，有可能出现同名情况。这里合并的时候统一读取判断处理下。
    ```
2. 合并 libs 目录
   - x86_64
   - arm64-v8a
3. 合并 assets 目录
4. 合并 AndroidManifest.xml 文件，去除重复的部分，例如权限
5. 合并 jar，把所有的 jar 文件复制到同一个 jars 中
#### 二、jar 转 smali 
1. jar 混淆合并
2. jar 转 dex
3. dex 转 smali

### 母包反编译
1. 反编译母包
2. 修改包名
3. 修改版本号
4. 修改版本名
5. 设置 minSdkVersion ，targetSdkVersion
6. 修改应用名称
7. 修改启动页
8. 修改 icon

## 渠道 SDK 调研
主要调研各个 SDK 需要对接的方法，生命周期等，抽象成统一的接口。这里只调客户端部分。
### oppo SDK
1. 初始化方法 ：oppo SDK 的初始化在应用的 Application 的 onCreate() 方法中。
2. 登录方法 : 登录方法的调用与回调统一为一个方法，通过代码块进行回调。
3. 获取 token 和 ssoid : 需要登录成功才行。
4. 支付 : 支付与登录类似，通过一个方法集成。
5. 退出引导 : 当游戏需要关闭或者退出时，需要调用 exit() 方法，回调成功后，结束游戏。
6. 上报游戏角色 : 这里是上报游戏角色信息的接口。
7. 获取实名制信息 :
8. 上报游戏数据 :
9. 获取用户信息 : 这里返回的为 oppo 的渠道数据信息。
10. 检查更新 : 检查 oppo 的软件商店是否有更新。menu
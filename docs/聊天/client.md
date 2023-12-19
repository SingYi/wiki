# Unity 解决方案
Unity 开发需要考虑 Unity Editor 的研发情况，因此，使用的技术栈必须要能够跨平台，因此有以下两个方向：

 - C++ 方向：不只可以 Unity 跨平台，其他平台也都可以，缺点是编译繁琐、Unity 调用的时候需要 C# 跨语言调用。
 - C# 方向：完美兼容 Unity 生态，缺点是只能兼容 Unity 生态。

## C# 解决方案
经过调研，C# 由一下几个解决方案。

 1. agsxmpp : 经过尝试，socket 连接都尚未连同，且库有点久远，推测已经无法兼容。
 2. Matrix.xmpp : 经过测试，控制台项目可以跑通，但是需要做 Unity 移植，依赖一个 system.linq 和 .nottey的库。

## Unity 添加 nuget
github : https://github.com/GlitchEnzo/NuGetForUnity

PackageManager里添加：
https://github.com/GlitchEnzo/NuGetForUnity.git?path=/src/NuGetForUnity

### DotNetty
https://github.com/Azure/DotNetty

## 尝试一
使用 Unity 2022.3 版本，安装 nuget，测试 dotnetty 在 Unity 中的应用。
可以使用，存在 ssl 证书问题。

## 尝试 xmpp 库
https://github.com/DmitryChabanin/xmpp.git
存在依赖问题

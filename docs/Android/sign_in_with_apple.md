# Sign in with Apple
Android 接入 Apple 账号登录。
目前 Apple 官方没有提供 Android 相关的接入接口，只能通过 web 的形式接入。

官方文档
 - [https://developer.apple.com/cn/sign-in-with-apple/get-started/]()https://developer.apple.com/cn/sign-in-with-apple/get-started/ 
 - [https://developer.apple.com/documentation/sign_in_with_apple/sign_in_with_apple_js/incorporating_sign_in_with_apple_into_other_platforms?changes=latest_minor](https://developer.apple.com/documentation/sign_in_with_apple/sign_in_with_apple_js/incorporating_sign_in_with_apple_into_other_platforms?changes=latest_minor)

官方文档中文：
 - [https://developer.apple.com/cn/help/account/configure-app-capabilities/configure-sign-in-with-apple-for-the-web/](https://developer.apple.com/cn/help/account/configure-app-capabilities/configure-sign-in-with-apple-for-the-web/)

# 创建标识符
## 步骤一：进入标识符页面
在“证书、标识符和描述文件” 中，点按边栏中的“标识符”，然后点按左上方的添加按钮 (+)。
这里如果是英文，点击 `identifiers`

## 步骤二：创建 Services ID
在 Register a new identifier 的菜单栏中选择 Services IDs 选项，然后点击 continue。

## 步骤三：输入说明(Description)与标识符(Identifier)
紧接着在 Description 输入框中输入说明
在 Identifier 输入框中数据唯一标识符

## 步骤四：注册(Register)服务标识符
点击 Register 按钮

## 步骤五：添加 Sign in with Apple 服务
点击刚刚注册好的标识符，进入详情界面，勾选上 Sign in with Apple 服务，然后点击 Configure（配置） 按钮。

## 步骤六：选取配套的 Appid
在弹出 Web Authentication Configuration 中，选择配套的 AppId 

## 步骤七：填写域名和返回 URL
网站域名、子域名、或返回 URL，必须提供至少一个域名或子域名。

## 步骤八：保存配置
点击 Done 以保存配置

## 步骤九：下一步
点击 Continue 继续下一步

## 步骤十：点击 Save
点击 Save 保存 Service ID 配置

https://beta.xyplay.cn/web-app-shop/
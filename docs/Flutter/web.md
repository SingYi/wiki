# flutter web
## 处理跨域问题
在 .vscode/launch.json 文件中添加如下配置
```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Flutter",
            "type": "dart",
            "request": "launch",
            "program": "lib/main.dart",
            "args": [
                "--web-browser-flag",
                "--disable-web-security",
                "--web-port",
                "8080"
            ]
        },
    ]
}
```
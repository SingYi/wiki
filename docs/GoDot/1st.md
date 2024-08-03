# 第一天

1. 安装 GoDot 4.2.2 版本
   - 踩坑， 需要注意电脑安装的 .net 版本，如果有冲突，需要卸载其他的 .net 版本重新安装， jetBrains 自动安装 .net 为全局生效。

## 场景
通过添加 node 节点在场景上实现游戏功能。


## 生命周期
1. _EnterTree : 场景添 node 进入树
2. _Ready ：装备完毕，可以进行相关初始化功能
3. _Process ：帧更新
4. _PhysicsProcess ：物理逻辑更新
5. _ExitTree ：移除销毁，通常进行析构
6. _Input : 监听输入事件，包括键盘和鼠标

## 鼠标和键盘输入
```csharp
public override void _Input(InputEvent @event)
	{
		base._Input(@event);
		// 判断是否为键盘事件
		if (@event is InputEventKey key)
		{
			if (key.Keycode == Key.K)
			{
				// 持续按压
				if (key.IsEcho())
				{
					GD.Print("持续按 k 键");
				} else if (key.IsPressed())
				{
					GD.Print("按下 k 键");
				}
				else if (key.IsReleased())
				{
					GD.Print("抬起 k 键");
				}
			}
		}
		
		// 鼠标事件
		if (@event is InputEventMouse)
		{
			var mouse = @event as InputEventMouse;
			if (mouse.IsPressed())
			{
				GD.Print(mouse.Position);
				GD.Print(mouse.ButtonMask);
			}
		}
	}
```

## 节点的寻找与获取
```csharp
        // 如果按下左键
        if (Input.IsActionJustPressed("left"))
        {
            // 获取当前场景的根节点
            Node root = this.GetTree().CurrentScene;
            // 寻找 test 节点
            Node test = root.FindChild("Test");
            // test.QueueFree();
            // test 从节点树中取出
            root.RemoveChild(test);
            // 将 test 添加到子节点
            this.AddChild(test);

            GetNode("/path");
        }
        
        if (Input.IsActionJustPressed("right"))
        {
            // 获取当前场景的根节点
            Node root = this.GetTree().CurrentScene;
            Node2D node2D = new Node2D();
            node2D.Name = "TTTTT";
            this.AddChild(node2D);
        }
```

## 场景的切换
```csharp
        // 如果按下左键
        if (Input.IsActionJustPressed("left"))
        {
            // 获取场景树
            SceneTree st = this.GetTree();
            // 场景跳转方法1
            // st.ChangeSceneToFile("res://game2.tscn");
            // 场景跳转方法2
            st.ChangeSceneToPacked(NewScene);
        }
        
        // 实例化一个场景,但是不加载,将里面的 node 加载到当前场景中
        if (Input.IsActionJustPressed("right"))
        {
            // 实例化场景
            Node node = NewScene.Instantiate();
            GetTree().CurrentScene.AddChild(node);
        }
```

## 永不销毁的脚本
1. 选择菜单栏的项目
2. 点击项目设置
3. 选择自动加载
4. 选择需要加载的脚本

> 适用于全局管理类. 是一个`单利`,切换场景也不会被销毁.

## 向量与标量
 - 标量:只有大小
<p align="center">
  <img src="https://img.icons8.com/fluency/96/server.png" alt="Simple Http Server Logo" width="96">
</p>

<h1 align="center">Simple Http Server</h1>

<p align="center">
  基于 Python 实现的轻量级 HTTP 文件服务器，专为 Unity 编辑器设计
</p>

<p align="center">
  <a href="https://github.com/AzathrixDev"><img src="https://img.shields.io/badge/GitHub-Azathrix-black.svg" alt="GitHub"></a>
  <a href="#"><img src="https://img.shields.io/badge/version-1.0.0-green.svg" alt="Version"></a>
  <a href="#license"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License"></a>
  <a href="https://unity.com/"><img src="https://img.shields.io/badge/Unity-6000.3+-black.svg" alt="Unity"></a>
</p>

---

## 特性

- 🚀 **一键启动** - 在 Unity 编辑器中直接启动/停止服务器
- 🌐 **Web 管理界面** - 浏览器中管理文件，支持上传、下载、删除
- 📁 **文件夹上传** - 支持整个文件夹的批量上传
- 🔄 **自动启动** - 可配置 Unity 启动时自动开启服务器
- 📝 **实时日志** - 编辑器窗口中显示操作日志，支持过滤和复制
- 💾 **进程持久化** - 服务器进程独立运行，关闭窗口不影响服务

## 安装

### 通过 Package Manager (Git URL)

1. 打开 `Window > Package Manager`
2. 点击 `+` > `Add package from git URL`
3. 输入：
```
https://github.com/AzathrixDev/com.azathrix.simple-http-server.git
```

### 通过 manifest.json

在 `Packages/manifest.json` 中添加：

```json
{
  "dependencies": {
    "com.azathrix.simple-http-server": "1.0.0"
  }
}
```

## 快速开始

### 1. 打开服务器窗口

菜单：`Azathrix > Http文件服务器`

### 2. 配置服务器

```
端口：8080（默认）
根目录：选择要托管的文件夹
```

### 3. 启动服务器

点击 **启动服务器** 按钮，然后点击 **打开管理页面** 在浏览器中管理文件。

### 代码中使用（可选）

```csharp
using Azathrix.SimpleHttpServer;

// 创建服务器实例
var server = new LocalHttpServer
{
    Port = 8080,
    RootDirectory = "D:/MyFiles"
};

// 监听日志
server.OnLog += message => Debug.Log(message);

// 启动
server.Start();

// 停止
server.Stop();
```

## 配置说明

| 配置项 | 说明 | 默认值 |
|--------|------|--------|
| 端口 | HTTP 服务器监听端口 | 8080 |
| 根目录 | 文件服务的根目录 | - |
| Unity启动时自动开启 | 是否在 Unity 启动时自动启动服务器 | false |
| 显示操作日志 | 是否在窗口中显示操作日志 | true |

## Web 管理界面

访问 `http://localhost:8080/`（端口根据配置）

| 功能 | 说明 |
|------|------|
| 浏览目录 | 点击文件夹名称进入子目录 |
| 上传文件 | 选择文件后点击"上传文件" |
| 上传文件夹 | 选择文件夹后点击"上传文件夹" |
| 新建文件夹 | 点击"新建文件夹"输入名称 |
| 删除 | 单个删除或勾选后批量删除 |
| 下载 | 点击文件名直接下载 |

## 典型用途

- **YooAsset 热更新** - 托管 AssetBundle 资源用于本地测试
- **资源服务器测试** - 模拟 CDN 环境进行开发调试
- **团队协作** - 局域网内快速分享文件

## 依赖

| 依赖 | 版本 | 说明 |
|------|------|------|
| Python | 3.x | 需要在系统 PATH 中 |
| Unity | 6000.3+ | 最低支持版本 |

> ⚠️ **注意**：请确保系统已安装 Python 3 并添加到环境变量 PATH 中。

## API 参考

### LocalHttpServer

| 属性/方法 | 类型 | 说明 |
|-----------|------|------|
| `Port` | int | 服务器端口 |
| `RootDirectory` | string | 根目录路径 |
| `IsRunning` | bool | 服务器是否运行中 |
| `OnLog` | event | 日志事件 |
| `Start()` | void | 启动服务器 |
| `Stop()` | void | 停止服务器 |
| `ReadNewLogs()` | string | 读取新的日志内容 |

### LocalServerSettings

| 属性 | 类型 | 说明 |
|------|------|------|
| `Port` | int | 端口配置 |
| `RootDirectory` | string | 根目录配置 |
| `AutoStartOnUnityOpen` | bool | 自动启动配置 |
| `ShowLogs` | bool | 显示日志配置 |

## License

MIT License

Copyright (c) 2024 Azathrix

# Vaultwarden Windows Binary Builder

[English](#english) | [中文](#chinese)

## English

This repository contains a GitHub Action that automatically builds and releases Windows binaries for [Vaultwarden](https://github.com/dani-garcia/vaultwarden).

### Features

- Automatically checks for new Vaultwarden releases
- Builds Windows binaries with SQLite support
- Creates GitHub releases with compiled binaries
- Runs every day at 2:00 AM UTC
- Statically linked for easy deployment

### Usage

1. Download the latest `.exe` file from the [Releases](https://github.com/your-username/Vaultwarden-Windows-Binary/releases) page
2. Download the web-vault files from [bw_web_builds releases](https://github.com/dani-garcia/bw_web_builds/releases)
3. Create the following directory structure:
   ```
   your-folder/
   ├── vaultwarden.exe
   └── web-vault/
       └── index.html
   ```
4. Create a batch file (e.g., `start-vaultwarden.bat`) with the following content:
   ```batch
   @echo off
   chcp 65001
   setlocal enabledelayedexpansion

   :: Set Rocket TLS configuration
   set ROCKET_TLS={certs="certificate.crt",key="private.key"}

   :: Set server address and port
   set ROCKET_ADDRESS=0.0.0.0
   set ROCKET_PORT=8443

   :: Set domain
   set DOMAIN=https://192.168.1.110:8443

   :: Display configuration for debugging
   echo Configuration:
   echo ROCKET_TLS=%ROCKET_TLS%
   echo ROCKET_ADDRESS=%ROCKET_ADDRESS%
   echo ROCKET_PORT=%ROCKET_PORT%
   echo DOMAIN=%DOMAIN%
   echo.

   :: Start Vaultwarden
   echo Starting Vaultwarden...
   vaultwarden.exe
   ```
5. Run the batch file to start Vaultwarden
6. Access via https://your-ip:8443 (default)

### Documentation

- [Vaultwarden Wiki (Chinese)](https://rs.ppgg.in/)

## Chinese

本仓库包含一个 GitHub Action，用于自动构建和发布 [Vaultwarden](https://github.com/dani-garcia/vaultwarden) 的 Windows 二进制文件。

### 功能特点

- 自动检查 Vaultwarden 新版本
- 构建支持 SQLite 的 Windows 二进制文件
- 创建包含编译后二进制文件的 GitHub 发布
- 每天 UTC 时间凌晨 2:00 自动运行
- 静态链接，便于部署

### 使用方法

1. 从 [Releases](https://github.com/your-username/Vaultwarden-Windows-Binary/releases) 页面下载最新的 `.exe` 文件
2. 从 [bw_web_builds releases](https://github.com/dani-garcia/bw_web_builds/releases) 下载 web-vault 文件
3. 创建以下目录结构：
   ```
   your-folder/
   ├── vaultwarden.exe
   └── web-vault/
       └── index.html
   ```
4. 创建批处理文件（例如：`start-vaultwarden.bat`），内容如下：
   ```batch
   @echo off
   chcp 65001
   setlocal enabledelayedexpansion

   :: 设置 Rocket TLS 配置
   set ROCKET_TLS={certs="certificate.crt",key="private.key"}

   :: 设置服务器地址和端口
   set ROCKET_ADDRESS=0.0.0.0
   set ROCKET_PORT=8443

   :: 设置域名
   set DOMAIN=https://192.168.1.110:8443

   :: 显示配置信息以便调试
   echo 配置信息:
   echo ROCKET_TLS=%ROCKET_TLS%
   echo ROCKET_ADDRESS=%ROCKET_ADDRESS%
   echo ROCKET_PORT=%ROCKET_PORT%
   echo DOMAIN=%DOMAIN%
   echo.

   :: 启动 Vaultwarden
   echo 正在启动 Vaultwarden...
   vaultwarden.exe
   ```
5. 运行批处理文件启动 Vaultwarden
6. 通过 https://your-ip:8443 访问（默认）

### 文档

- [Vaultwarden Wiki（中文）](https://rs.ppgg.in/) 

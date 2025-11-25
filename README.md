# Komari Agent - s390x

基于原仓库 [komari-monitor/komari-agent](https://github.com/komari-monitor/komari-agent) 添加了对 **Linux s390x (IBM Z)** 架构的支持。

## 功能特性

- 🖥️ s390x 架构预编译二进制文件
- 🐳 s390x 架构 Docker 镜像 (推送至 GitHub Container Registry)
- 🔄 自动化发布流程

## 安装

### 二进制文件

从 [Releases](../../releases) 页面下载：

```bash
# 创建目录
sudo mkdir -p /opt/komari-agent
# 下载文件并保存为 /opt/komari-agent/komari-agent
sudo curl -L -o /opt/komari-agent/komari-agent https://github.com/lizhenmiao/komari-agent-s390x/releases/download/1.1.34/komari-agent-linux-s390x
# 给文件添加执行权限
sudo chmod +x /opt/komari-agent/komari-agent
# 进入文件夹
cd /opt/komari-agent
# 运行文件
nohup ./komari-agent -e http://127.0.0.1:8080 -t 1234567890abcdef > komari.log 2>&1 &
```

### Docker

镜像托管在 GitHub Container Registry：

```bash
# 拉取镜像
docker pull ghcr.io/lizhenmiao/komari-agent:latest

# 运行
docker run -d ghcr.io/lizhenmiao/komari-agent:latest
```

## CI/CD

手动触发工作流，输入上游项目的 tag 版本号：
1. 拉取上游 komari-agent 对应 tag 的代码
2. 构建 s390x 二进制文件
3. 创建 Release 并上传二进制文件
4. 构建并推送 s390x Docker 镜像至 ghcr.io

### aemu_postoffice

PSP Ad Hoc 数据转发协议及其实现，旨在通过互联网提供简单、可靠的 Ad Hoc 联机体验。

本项目基于 [aemu_postoffice](https://github.com/Kethen/aemu_postoffice.git) 的一个早期版本进行分支维护，并保留了该版本的集中处理模型。这是因为上游项目后续 TypeScript 版本引入的并发处理逻辑，在《最终幻想纷争 012》的多人联机机制下会产生额外延迟。

目前使用该项目的客户端：

- [PSP 互联网 Ad Hoc 插件 aemu](https://github.com/kethen/aemu)
- [PPSSPP](http://github.com/hrydgard/ppsspp)

#### 当前设计

参见 [design.md](/design.md)

#### 客户端实现

参见 [./client/postoffice.c](/client/postoffice.c)

##### 构建与测试

Linux：

```
# Ubuntu/Debian：
apt install podman git

# OpenSUSE
zypper install podman git

# Fedora
dnf install podman git

# 克隆项目并构建客户端
git clone https://github.com/kethen/aemu_postoffice
cd aemu_postoffice/client
bash build_podman.sh

# 运行测试；需要在本机启动中继服务器（见下文）
./test.out
```

Windows：

1. 安装 https://cygwin.com/，并选择 `mingw64-x86_64-gcc`、`mingw64-x86_64-gcc-g++` 和 `git` 软件包
2. 打开 Cygwin Shell

```
# 克隆项目并构建客户端
git clone https://github.com/kethen/aemu_postoffice
cd aemu_postoffice/client
bash build_windows.sh

# 运行测试；需要在本机启动中继服务器（见下文）
./test.exe
```

#### 服务端实现

参见 [./server_njs/aemu_postoffice.ts](/server_njs/aemu_postoffice.ts)

##### 运行服务端

参见 [./server_njs/usage.md](/server_njs/usage.md)

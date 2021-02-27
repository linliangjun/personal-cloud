# 在 Windows 上安装 Docker

## 系统要求

### Windows 10

若要在 Windows 10 上运行容器，需要以下条件

- Windows 10 专业版或企业版（1607 或更高版本）
- 启用 Hyper-V 功能

### Windows Server

若要在 Windows Server 上运行容器，需要一台运行 Windows Server（半年频道）、Windows Server 2019 或 Windows Server 2016 的物理服务器或虚拟机。

在 Windows Server

### WSL 2

WSL 2 是适用于 Linux 的 Windows 子系统体系结构的一个新版本，它支持适用于 Linux 的 Windows 子系统在 Windows 上运行 ELF64 Linux 二进制文件。 它的主要目标是 **提高文件系统性能**，以及添加 **完全的系统调用兼容性**，因此在 WSL 2 中安装 Docker 就和 Linux 中一样。

安装 WSL 2 请参考 [在 Windows 10 上安装适用于 Linux 的 Windows 子系统（WSL）](https://github.com/linliangjun/personal-cloud/blob/main/notes/wsl/wsl-install-win10.md)

在 Linux 上安装 Docker 请参考 [在 Linux 上安装 Docker](https://github.com/linliangjun/personal-cloud/blob/main/notes/docker/docker-install-linux.md)

## 安装 Docker

### Windows 10

下载并安装 [Docker Desktop](https://desktop.docker.com/win/stable/Docker%20Desktop%20Installer.exe) 桌面程序，安装完成后切换容器类型为 Windows 容器。

 <img alt="docker-for-win-switch" src="https://raw.githubusercontent.com/linliangjun/personal-cloud/main/images/docker/docker-install-win-step01.png" width=300 height=300>

### Windows Server

1. 打开具有管理员权限的 PowerShell，从 PowerShell 安装 Docker-Microsoft PackageManagement 提供程序。

   ```powershell
   Install-Module -Name DockerMsftProvider -Repository PSGallery -Force
   ```

   如果系统提示安装 NuGet 提供程序，输入 `Y` 进行安装。

2. 使用 PackageManagement PowerShell 模块安装最新版本的 Docker。

   ```powershell
   Install-Package -Name docker -ProviderName DockerMsftProvider
   ```

   PowerShell 询问是否信任包源“DockerDefault”时，输入 `A` 以继续进行安装。

3. 在安装完成后重启计算机。

   ```powershell
   Restart-Computer -Force
   ```

## 参考文章

1. [Microsoft：准备 Windows 操作系统容器](https://docs.microsoft.com/zh-cn/virtualization/windowscontainers/quick-start/set-up-environment?tabs=Windows-Server)
2. [Microsoft：什么是WSL 2](https://docs.microsoft.com/zh-cn/windows/wsl/about#what-is-wsl-2)
# 在 Windows 10 上安装适用于 Linux 的 Windows 子系统（WSL）

有两种方式可以安装适用于 Linux 的 Windows 子系统

- **[手动安装](#manual-installation-steps)**：可以在任意版本的 Windows 10 上安装 Linux。

- **[简化安装](#simplified-installation-for-windows-insiders)** ：需要加入 [Windows 预览体验计划](https://insider.windows.com/getting-started) 并安装 Windows 10 的预览版（20262 或更高版本），但不需要执行手动安装步骤。

## <span id="manual-installation-steps">手动安装</span>

1. **启用 Windows 功能**

   在 Windows 功能的窗口中，启用 **适用于 Linux 的 Windows 子系统** 和 **虚拟机平台** 功能，之后重启计算机。

    <img alt="enable wsl and/or virtual machine feature" src="https://raw.githubusercontent.com/linliangjun/personal-cloud/main/images/wsl/wsl-install-win10-step01.png" width=400 height=400>
   

   > 1. 若只想安装 WSL 1，那么无需启用 **虚拟机平台** 功能。
   >
   > 2. 安装 WSL 2 需要操作系统为 Windows 10 1903（内部版本 18362）或更高版本。

2. **升级到 WSL 2**

   下载更新包

    - [适用于 x64 计算机的 WSL 2 更新包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
    - [适用于 ARM64 计算机的 WSL 2 更新包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)

   将 WSL 2 设为默认版本，打开 PowerShell 执行命令

   ```powershell
   wsl --set-default-version 2
   ```

3. **安装 Linux 发行版**

   打开 Microsoft Store，搜索 linux，按喜好安装 Linux 发行版。

    <img alt="install your Linux distribution on microsoft store" src="https://raw.githubusercontent.com/linliangjun/personal-cloud/main/images/wsl/wsl-install-win10-step02.png" width=600 height=412>
   
   > 如果无法使用 Microsoft Store，可以通过单击以下链接来下载并手动安装 Linux 发行版
    > - [Ubuntu 20.04](https://aka.ms/wslubuntu2004)
    > - [Ubuntu 20.04 ARM](https://aka.ms/wslubuntu2004arm)
    > - [Ubuntu 18.04](https://aka.ms/wsl-ubuntu-1804)
    > - [Ubuntu 18.04 ARM](https://aka.ms/wsl-ubuntu-1804-arm)
    > - [Ubuntu 16.04](https://aka.ms/wsl-ubuntu-1604)
    > - [Debian GNU/Linux](https://aka.ms/wsl-debian-gnulinux)
    > - [Kali Linux](https://aka.ms/wsl-kali-linux-new)
    > - [OpenSUSE Leap 42](https://aka.ms/wsl-opensuse-42)
    > - [SUSE Linux Enterprise Server 12](https://aka.ms/wsl-sles-12)
    > - [Fedora Remix for WSL](https://github.com/WhitewaterFoundry/WSLFedoraRemix/releases)
    > 
    > 然后打开 PowerShell 并定位到包含 Linux 发行版的文件夹，运行命令
    >
    > ```powershell
    > Add-AppxPackage .\app_name.appx
    > ```
    > 
    > 其中 `app_name.appx` 是发行版的文件名


## <span id="simplified-installation-for-windows-insiders">简化安装</span>

使用简化安装，必须加入 [Windows 预览体验计划](https://insider.windows.com/getting-started) 并安装 Windows 10 的预览版（20262 或更高版本），然后按如下步骤安装

1. 打开具有管理员权限的 PowerShell，执行命令 `wsl.exe --install`

2. 重启计算机

## 参考文章

1. [Microsoft：适用于 Linux 的 Windows 子系统安装指南 (Windows 10)](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10)
2. [Microsoft：手动下载适用于 Linux 的 Windows 子系统发行版包](https://docs.microsoft.com/zh-cn/windows/wsl/install-manual)
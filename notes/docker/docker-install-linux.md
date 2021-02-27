# 在 Linux 上安装 Docker

Linux 使用包管理器来管理软件，不过默认的源可能没有 Docker 或者版本老旧，因此我们要额外添加一个源。

> 由于 Linux 有众多的发行版，未列出的项请查看 [Install Docker Engine](https://docs.docker.com/engine/install/)

## Ubuntu

操作系统要求：Ubuntu Groovy 20.10 或更高版本、Ubuntu 长期支持版 16.04/18.04/20.04（LTS）

如果之前安装过 Docker，请先卸载 Docker

```bash
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

1. **添加源的 GPG 密钥并验证指纹**

   ```bash
   $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   $ sudo apt-key fingerprint 0EBFCD88
   
   pub   rsa4096 2017-02-22 [SCEA]
         9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
   uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
   sub   rsa4096 2017-02-22 [S]
   ```

2. **添加源**

   ```bash
   $ sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"
   ```

   >使用国内的源可以提升下载的速度（替换 https 内容即可）
   >
   >1. 清华大学源：https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu
   >2. 中科大源：https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu
   >3. 阿里云源：http://mirrors.aliyun.com/docker-ce/linux/ubuntu

3. **安装并运行最新版本的 Docker**

   ```bash
   $ sudo apt-get update
   $ sudo apt-get install docker-ce docker-ce-cli containerd.io
   $ sudo service docker start
   $ sudo docker version
   ```

## 参考文章

1. [Docker：Install Docker Engine](https://docs.docker.com/engine/install/)
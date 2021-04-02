# 在 Linux 上安装 Docker

Linux 使用包管理器来管理软件，不过默认的源可能没有 Docker 或者版本老旧，因此我们要额外添加一个源。另外，国内用户使用 Docker 默认的镜像源可能会被限制，因此需要设置为国内的镜像源。

> 由于 Linux 有众多的发行版，未列出的项请查看 [Install Docker Engine](https://docs.docker.com/engine/install/)。
>
> 源和镜像源不要混淆，前者所属于包管理器，用于下载软件；后者所属于 Docker，用于下载镜像。

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

4. **设置镜像源**

   以中科大镜像源为例
   ```bash
   $ sudo vim /etc/docker/daemon.json

   {
      "registry-mirrors":[
         "https://docker.mirrors.ustc.edu.cn"
      ]
   }
   ```
   > 国内其它的镜像源
   >
   >1. 网易镜像源：https://hub-mirror.c.163.com
   >2. 七牛云镜像源：https://reg-mirror.qiniu.com
   
## 参考文章

1. [Docker：Install Docker Engine](https://docs.docker.com/engine/install/)
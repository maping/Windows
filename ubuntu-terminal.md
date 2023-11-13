# Ubuntu Terminal

## 1. 安装
在 Microsoft Store 搜索 linux，安装过程中创建你的个人用户，比如：maping/maping，并记住

## 2. 进入 Ubuntu Terminal
Win + R，然后输入 ubuntu 输入个人账户的口令，进入个人账户主目录：/home/maping

## 3. 在 Ubuntu Terminal 中安装软件

### 3.1 安装 docker 
安装完 Docker Desktop for Windows 后，发现在 ubuntu terminal 中 docker 也已经安装
```console
$ docker --version
Docker version 24.0.6, build ed223bc
$ which docker
$ ll /usr/bin/docker
lrwxrwxrwx 1 root root 48 Jun  6 22:13 /usr/bin/docker -> /mnt/wsl/docker-desktop/cli-tools/usr/bin/docker*
```
>注意：发现跟 cmd terminal 中的 Docker 版本一致，以后更新 Docker Desktop for Windows，ubuntu terminal 中的 Docker 也会随之更新。

### 3.2 安装 kubectl

#### 3.2.1 Docker 自带的 kubectl
安装完 Docker Desktop for Windows 后，发现也会在 ubuntu terminal 中安装一个 kubectl
```console
$ which kubectl
/usr/local/bin/kubectl
$ ll /usr/local/bin/kubectl
lrwxrwxrwx 1 root root 55 Jun  6 22:13 /usr/local/bin/kubectl -> /mnt/wsl/docker-desktop/cli-tools/usr/local/bin/kubectl*
$ kubectl version --client -o yaml
clientVersion:
  buildDate: "2023-09-13T09:35:49Z"
  compiler: gc
  gitCommit: 89a4ea3e1e4ddd7f7572286090359983e0387b2f
  gitTreeState: clean
  gitVersion: v1.28.2
  goVersion: go1.20.8
  major: "1"
  minor: "28"
  platform: windows/amd64
kustomizeVersion: v5.0.4-0.20230601165947-6ce0bf390ce3
```
>重要：kubectl 在 Windows 10 下的 cmd terminal 和 ubuntu terminal 之间彼此是不通的。

>重要：连上 VPN 后，不能访问外网（原因不明），因此无法连接 EKS 集群，必须断开才能连。

#### 3.2.2 单独下载并安装 kubectl
```console
$ curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt
v1.28.3
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.28.3/bin/linux/amd64/kubectl" # 在 cmd termial 中执行
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
$ mkdir software && cd software
$ cp /mnt/c/Users/vmaping/kubectl .
```
#### 3.2.3 修改 ~/.bashrc
```console
$ echo 'export PATH=/home/maping/software:$PATH' >>~/.bashrc
$ echo 'alias k=kubectl' >>~/.bashrc
$ source ~/.bashrc
$ kubectl version --client -o yaml
clientVersion:
  buildDate: "2023-10-18T11:42:52Z"
  compiler: gc
  gitCommit: a8a1abc25cad87333840cd7d54be2efaf31a3177
  gitTreeState: clean
  gitVersion: v1.28.3
  goVersion: go1.20.10
  major: "1"
  minor: "28"
  platform: linux/amd64
kustomizeVersion: v5.0.4-0.20230601165947-6ce0bf390ce3
```
>说明：设置 PATH 环境变量后，可以看到 kubectl 使用的是单独下载的 kubectl。

#### 3.2.4 复制 ~/.kube/config
把 cmd 下的.kube/config 文件复制过来
```console
$ cd ~/.kube/
$ cp /mnt/c/Users/vmaping/.kube/config . 
```

### 3.3 安装 [eksctl](https://github.com/eksctl-io/eksctl)
```console
$ tar -zxvf eksctl_Linux_amd64.tar.gz
$ sudo mv eksctl /usr/local/bin
$ eksctl version
0.164.0
```

### 3.4 安装 [helm](https://github.com/helm/helm）
```console
$ curl "https://get.helm.sh/helm-v3.13.2-linux-amd64.tar.gz" -o "helm-v3.13.2-linux-amd64.tar.gz" # 在 cmd 中执行
$ mv /mnt/c/Users/vmaping/helm-v3.13.2-linux-amd64.tar.gz . 
$ tar -zxvf helm-v3.13.2-linux-amd64.tar.gz
$ sudo mv linux-amd64/helm /usr/local/bin
$ helm version
version.BuildInfo{Version:"v3.13.2", GitCommit:"2a2fb3b98829f1e0be6fb18af2f6599e0f4e8243", GitTreeState:"clean", GoVersion:"go1.20.10"}
```

### 3.5 安装 [k9s](https://github.com/derailed/k9s) 
```console
$ curl -LO https://github.com/derailed/k9s/releases/download/v0.28.2/k9s_Linux_amd64.tar.gz # 在 cmd termial 中执行
$ mv /mnt/c/Users/vmaping/k9s_Linux_amd64.tar.gz . 
$ tar -zxvf k9s_Linux_amd64.tar.gz
$ sudo mv k9s /usr/local/bin
$ k9s version
 ____  __.________
|    |/ _/   __   \______
|      < \____    /  ___/
|    |  \   /    /\___ \
|____|__ \ /____//____  >
        \/            \/

Version:    v0.28.2
Commit:     694159b857314de5b69f251e42a5931f32105cb8
Date:       2023-11-12T06:19:0
```

### 3.6 安装 [kind](https://github.com/kubernetes-sigs/kind) 
```console
$ curl -LO https://github.com/kubernetes-sigs/kind/releases/download/v0.20.0/kind-linux-amd64  # 在 cmd termial 中执行
$ mv /mnt/c/Users/vmaping/kind-linux-amd64 . 
$ mv kind-linux-amd64 kind
$ sudo mv kind /usr/local/bin
$ kind version
kind v0.20.0 go1.20.4 linux/amd64
```

### 3.7 安装并配置 [eks-node-viewer](https://github.com/awslabs/eks-node-viewer) 
```console
$ curl -LO https://github.com/awslabs/eks-node-viewer/releases/download/v0.5.0/eks-node-viewer_Linux_x86_64 # 在 cmd termial 中执行
$ mv /mnt/c/Users/vmaping/eks-node-viewer_Linux_x86_64 . 
$ mv eks-node-viewer_Linux_x86_64 eks-node-viewer
$ sudo mv eks-node-viewer /usr/local/bin
$ eks-node-viewer --version
eks-node-viewer version 0.5.0
commit: 952534dd822c3005efd1e625022067fd2f05b5b5
built at: 2023-10-20T18:18:31Z
built by: goreleaser
```

### 3.8 安装 AWS CLI
```console
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" # 在 cmd 中执行
$ mv /mnt/c/Users/vmaping/awscliv2.zip . 
$ unzip awscliv2.zip
$ sudo ./aws/install # 新装
$ sudo ./aws/install --update # 升级
$ aws --version
aws-cli/2.13.26 Python/3.11.6 Linux/5.10.102.1-microsoft-standard-WSL2 exe/x86_64.ubuntu.20 prompt/off
```
>注意：下载时不能连接 VPN，否则 DNS 无法解析。

更新 AWS CLI
```console
$ sudo ./aws/install --update
You can now run: /usr/local/bin/aws --version
```

### 3.9 安装 gpg
```console
$ gpg --gen-key
gpg (GnuPG) 2.2.19; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: Ma Ping
Email address: maping930883@hotmail.com
You selected this USER-ID:
    "Ma Ping <maping930883@hotmail.com>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: /home/maping/.gnupg/trustdb.gpg: trustdb created
gpg: key 621951D36E86937A marked as ultimately trusted
gpg: directory '/home/maping/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/maping/.gnupg/openpgp-revocs.d/1714CDEB64509317CD142F76621951D36E86937A.rev'
public and secret key created and signed.

pub   rsa3072 2023-09-01 [SC] [expires: 2025-08-31]
      1714CDEB64509317CD142F76621951D36E86937A
uid                      Ma Ping <maping930883@hotmail.com>
sub   rsa3072 2023-09-01 [E] [expires: 2025-08-31]
$ gpg --detach-sign sms-pricing-20230901.pdf

$ gpg --verify sms-pricing-20230901.pdf.sig
gpg: assuming signed data in 'sms-pricing-20230901.pdf'
gpg: Signature made Fri Sep  1 10:48:36 2023 CST
gpg:                using RSA key 1714CDEB64509317CD142F76621951D36E86937A
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
gpg: next trustdb check due at 2025-08-31
gpg: Good signature from "Ma Ping <maping930883@hotmail.com>" [ultimate]
```

## 4. 疑问
- Ubuntu Terminal 原理，内嵌了一个 Ubuntu 在 Windows 中，那里面做的操作怎么保留 ？
- 卸载 Ubuntu Terminal，所有东西都没了？
- 不能访问谷歌，即使连了 VPN 也不行？
- 不能使用 ping ？

## Reference
- [Windows10安装Ubuntu桌面子系统](https://www.jianshu.com/p/2bcf5eca5fbc)
- [windows 10 WSL ubuntu unable to ping anything](https://superuser.com/questions/1358297/windows-10-wsl-ubuntu-unable-to-ping-anything)
- [How to Install Linux Software in Windows 10’s Ubuntu Bash Shell](https://www.howtogeek.com/261449/how-to-install-linux-software-in-windows-10s-ubuntu-bash-shell/)

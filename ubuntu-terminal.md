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
```console
$ curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt
1.24.1
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.24.1/bin/linux/amd64/kubectl"
 % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 43.5M  100 43.5M    0     0  11.6M      0  0:00:03  0:00:03 --:--:-- 11.6M
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
 % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 43.5M  100 43.5M    0     0  7237k      0  0:00:06  0:00:06 --:--:-- 9018k
```
为 kubectl 设置 alias: k
```console
$ echo 'alias k=kubectl' >>~/.bashrc
$ source ~/.bashrc
```
### 3.3 安装 eksctl
查看当前最新版本：https://github.com/eksctl-io/eksctl
```console
$ tar -zxvf eksctl_Linux_amd64.tar.gz
$ sudo mv eksctl /usr/local/bin
$ eksctl version
0.160.0
```
### 3.4 安装 helm
查看当前最新版本：https://github.com/helm/helm/releases
```console
$ wget https://get.helm.sh/helm-v3.12.3-linux-amd64.tar.gz
$ tar -zxvf helm-v3.12.3-linux-amd64.tar.gz
$ sudo mv linux-amd64/helm /usr/local/bin
$ helm version
version.BuildInfo{Version:"v3.12.3", GitCommit:"3a31588ad33fe3b89af5a2a54ee1d25bfe6eaa5e", GitTreeState:"clean", GoVersion:"go1.20.7"}
```
### 3.5 安装 AWS CLI
```console
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" # 在 cmd 中执行
$ mv /mnt/c/Users/vmaping/awscliv2.zip . 
$ unzip awscliv2.zip
$ sudo ./aws/install # 新装
$ sudo ./aws/install --update # 升级
$ /usr/local/bin/aws --version
aws-cli/2.13.24 Python/3.11.5 Linux/5.10.102.1-microsoft-standard-WSL2 exe/x86_64.ubuntu.20 prompt/off
```
>注意：不能连接 VPN，否则 DNS 无法解析。

更新 AWS CLI
```console
$ sudo ./aws/install --update
You can now run: /usr/local/bin/aws --version
```

### 3.6 安装 gpg
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

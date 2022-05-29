# Ubuntu Terminal

## 1. 安装
在 Microsoft Store 搜索 linux，安装过程中创建你的个人用户，比如：maping/maping，并记住

## 2. 进入 Ubuntu Terminal
Win + R，然后输入 ubuntu 输入个人账户的口令，进入个人账户主目录：/home/maping

## 3. 在 Ubuntu Terminal 中安装软件

### 3.1 安装 kubectl
```console
$ curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt
1.24.1
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.24.1/bin/linux/amd64/kubectl"
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
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

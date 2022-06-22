# Windows 下开发环境设置 (2022-06-22 更新)

## 1. 一键显示环境变量窗口 ✅
1. 桌面创建快捷方式，Target 输入: rundll32.exe sysdm.cpl,EditEnvironmentVariables
2. 右键 Run as administrator，可以添加修改 System Variables

## 2. 安装 Git ✅
- 下载 [Git](https://git-scm.com/download/win) 
-	检查安装是否正确：打开 cmd 命令窗口，输入 `git --version`
``` console
$ git --version
git version 2.36.1.windows.1
```

## 3. 安装和配置 FileZilla ✅
- 下载 [FileZilla](https://filezilla-project.org/download.php) 
>注意: 不能直接下载 .exe 文件，安全检查会报告有 virus，可以下载 FileZilla_3.60.1_win64.zip。

## 4. 安装和配置 MobaXterm ✅
- 下载 [MobaXterm](https://mobaxterm.mobatek.net/download.html) 
>说明：下载 MobaXterm_Portable_v22.0.zip

## 5. 安装和配置 WinSCP ✅
- 下载 [WinSCP 5.19.6](https://winscp.net/eng/download.php) 

## 3. Java 开发环境

### 3.1 安装和配置 Open JDK ✅
- 下载 [Open JDK](https://openjdk.java.net/)
- 解压缩：openjdk-17+35_windows-x64_bin.zip
- 设置环境变量 JAVA_HOME，例如：C:\Software\java\openjdk
- 设置环境变量 PATH，增加一条，%JAVA_HOME%\bin
- 检查安装是否正确：打开一个 cmd 窗口，输入 `java -version`

``` console
$ java -version
Picked up JAVA_TOOL_OPTIONS: -Dlog4j2.formatMsgNoLookups=true
openjdk version "17" 2021-09-14
OpenJDK Runtime Environment (build 17+35-2724)
OpenJDK 64-Bit Server VM (build 17+35-2724, mixed mode, sharing)
```

### 3.2 安装和配置 Ant ✅
- 下载 [Ant](https://ant.apache.org/bindownload.cgi)
- 解压缩：apache-ant-1.10.12-bin.zip
- 设置环境变量 ANT_HOME，例如：C:\Software\apache\ant
- 设置环境变量 PATH，增加一条，%ANT_HOME%\bin
- 检查安装是否正确：打开一个 cmd 窗口，输入 `ant -version`
``` console
$ ant -version
Picked up JAVA_TOOL_OPTIONS: -Dlog4j2.formatMsgNoLookups=true
Apache Ant(TM) version 1.10.12 compiled on October 13 2021
```

### 3.3 安装和配置 Maven ✅
- 下载 [Maven](https://maven.apache.org/download.cgi)
- 解压缩：apache-maven-3.8.5-bin.zip
- 设置环境变量 M2_HOME，例如：C:\Software\apache\maven
- 设置环境变量 PATH，增加一条，%M2_HOME%\bin 
- 设置环境变量 MAVEN_OPTS，例如：-Xms512m -Xmx1024m
- 检查安装是否正确：打开 cmd 命令窗口，`mvn -version`
``` console
$ mvn -version
Picked up JAVA_TOOL_OPTIONS: -Dlog4j2.formatMsgNoLookups=true
Apache Maven 3.8.5 (3599d3414f046de2324203b78ddcf9b5e4388aa0)
Maven home: C:\Software\Apache\maven
Java version: 17, vendor: Oracle Corporation, runtime: C:\Software\java\openjdk
Default locale: en_US, platform encoding: GBK
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"
```

## 4. .NET 开发环境

### 4.1 .NET Framework 开发环境 ✅
下载并安装 Vistual Studio 2019

### 4.2 .NET Core | .NET 6 开发环境
下载并安装 Vistual Studio 2022

## 5. Python 开发环境

## 6. Go 开发环境

## 7. 容器开发环境 ✅

### 7.1 Install Linux on Windows with WSL
[Install Linux on Windows with WSL](https://docs.microsoft.com/en-us/windows/wsl/install) 是安装 Docker 的前置条件。

以管理员身份打开 cmd terminal
```console
C:\Windows\system32>wsl --install
Installing: Virtual Machine Platform
Virtual Machine Platform has been installed.
Installing: Windows Subsystem for Linux
Windows Subsystem for Linux has been installed.
Downloading: WSL Kernel
Installing: WSL Kernel
WSL Kernel has been installed.
Downloading: Ubuntu
The requested operation is successful. Changes will not be effective until the system is rebooted.
```
>重要：重启机器，然后 ubuntu 会继续安装，输入用户名 maping/maping。

默认 WSL 安装的是 Ubuntu，要想安装其它 Linux，首先查看可以安装的 Linux 列表
```console
wsl --list --online
The following is a list of valid distributions that can be installed.
Install using 'wsl --install -d <Distro>'.

NAME            FRIENDLY NAME
Ubuntu          Ubuntu
Debian          Debian GNU/Linux
kali-linux      Kali Linux Rolling
openSUSE-42     openSUSE Leap 42
SLES-12         SUSE Linux Enterprise Server v12
Ubuntu-16.04    Ubuntu 16.04 LTS
Ubuntu-18.04    Ubuntu 18.04 LTS
Ubuntu-20.04    Ubuntu 20.04 LTS
```

### 7.2 安装和配置 Docker Desktop ✅
>重要：Docker for Windows 目前只支持在服务支持期内的 Windows 10 。

- 下载 [Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/install/) 
- 双击 Docker Desktop Installer.exe 开始安装，安装过程保持默认选项即可
- 检查安装是否正确：打开 cmd 命令窗口，`docker --version`
``` console
$ docker --version
Docker version 20.10.16, build aa7e414
$ where docker
C:\Program Files\Docker\Docker\resources\bin\docker
C:\Program Files\Docker\Docker\resources\bin\docker.exe
```
- 运行 helloworld：打开 cmd 命令窗口，`docker run hello-world`
``` console
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete
Digest: sha256:80f31da1ac7b312ba29d65080fddf797dd76acfb870e677f390d5acba9741b17
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
 ``` 

打开 Docker Desktop，勾选 Kubernetes -> Enable Kubernetes，Apply & Restart
```console
$ kubectl get nodes
NAME             STATUS   ROLES           AGE     VERSION
docker-desktop   Ready    control-plane   2m57s   v1.24.0
```
>说明： Enable Kubernetes 后，会发现有一个单节点的 Kubernetes Cluster。

### 7.3 在 ubuntu terminal 中确认 docker 也已经安装 ✅
``` console
$ docker --version
Docker version 20.10.16, build aa7e414
$ which docker
$ ll /usr/bin/docker
lrwxrwxrwx 1 root root 48 Jun  6 22:13 /usr/bin/docker -> /mnt/wsl/docker-desktop/cli-tools/usr/bin/docker*
```
>注意：发现跟 cmd terminal 中的 Docker 版本一致，那以后更新 Docker Desktop for Windows，是不是 ubuntu terminal 中的 Docker 也会随之更新？

### 7.4 安装 kubectl ✅
- [Install kubectl binary with curl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)
- 查看 kubectl 最新稳定版: https://storage.googleapis.com/kubernetes-release/release/stable.txt 
- 科学下载 kubectl
    - https://storage.googleapis.com/kubernetes-release/release/VERSION-TAG/bin/OS/ARCH/kubectl.exe 
    - 比如：curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.24.1/bin/windows/amd64/kubectl.exe
    - VERSION-TAG 取值为版本号，比如：v1.24.1
    - OS 取值可以为 darwin, linux, windows
    - ARCH 取值可以为 386, amd64
- 设置环境变量 PATH，增加一条，C:\Software\Google\Kubernetes 
- 检查安装是否正确：打开 cmd 命令窗口，```kubectl version -o yaml```
```console
$ kubectl version -o yaml
clientVersion:
  buildDate: "2022-05-24T12:26:19Z"
  compiler: gc
  gitCommit: 3ddd0f45aa91e2f30c70734b175631bec5b5825a
  gitTreeState: clean
  gitVersion: v1.24.1
  goVersion: go1.18.2
  major: "1"
  minor: "24"
  platform: windows/amd64
kustomizeVersion: v4.5.4

Unable to connect to the server: dial tcp [::1]:8080: connectex: No connection could be made because the target machine actively refused it.
```

Docker Desktop for Windows 本身自带 kubectl
```console
$ where kubectl
C:\Software\Google\Kubernetes\kubectl.exe
C:\Program Files\Docker\Docker\resources\bin\kubectl.exe
$ cd C:\Program Files\Docker\Docker\resources\bin
$ kubectl version -o yaml
clientVersion:
  buildDate: "2022-05-03T13:46:05Z"
  compiler: gc
  gitCommit: 4ce5a8954017644c5420bae81d72b09b735c21f0
  gitTreeState: clean
  gitVersion: v1.24.0
  goVersion: go1.18.1
  major: "1"
  minor: "24"
  platform: windows/amd64
kustomizeVersion: v4.5.4

Unable to connect to the server: dial tcp [::1]:8080: connectex: No connection could be made because the target machine actively refused it.
```
>注意：请把手工安装的 kubectl 的 PATH 项放到 Docker Desktop 安装程序所添加的目录之前，或者干脆删除 Docker Desktop 所安装的 kubectl。
 
### 7.5 在 ubuntu terminal 中确认 kubectl 也已经安装 ✅
Docker Desktop for Windows 也会在 ubuntu terminal 中安装一个 kubectl
```console
$ which kubectl
/usr/local/bin/kubectl
$ ll /usr/local/bin/kubectl
lrwxrwxrwx 1 root root 55 Jun  6 22:13 /usr/local/bin/kubectl -> /mnt/wsl/docker-desktop/cli-tools/usr/local/bin/kubectl*
```
>重要：kubectl 在 Windows 10 下的 cmd terminal 和 ubuntu terminal 之间彼此是不通的。

### 7.6 安装 [kind](https://kind.sigs.k8s.io/)

直接下载 [kind-windows-amd64](https://github.com/kubernetes-sigs/kind)，改名为 kind.exe，放到 PATH 路径下。

创建 Kubernetes Cluster: dev
```console
$ kind create cluster --name dev
Creating cluster "dev" ...
 • Ensuring node image (kindest/node:v1.24.0) 🖼  ...
 ✓ Ensuring node image (kindest/node:v1.24.0) 🖼
 • Preparing nodes 📦   ...
 ✓ Preparing nodes 📦
 • Writing configuration 📜  ...
 ✓ Writing configuration 📜
 • Starting control-plane 🕹️  ...
 ✓ Starting control-plane 🕹️
 • Installing CNI 🔌  ...
 ✓ Installing CNI 🔌
 • Installing StorageClass 💾  ...
 ✓ Installing StorageClass 💾
Set kubectl context to "kind-dev"
You can now use your cluster with:

kubectl cluster-info --context kind-dev

Have a nice day! 👋
```
创建 Kubernetes Cluster: test
```console
Creating cluster "test" ...
 • Ensuring node image (kindest/node:v1.24.0) 🖼  ...
 ✓ Ensuring node image (kindest/node:v1.24.0) 🖼
 • Preparing nodes 📦   ...
 ✓ Preparing nodes 📦
 • Writing configuration 📜  ...
 ✓ Writing configuration 📜
 • Starting control-plane 🕹️  ...
 ✓ Starting control-plane 🕹️
 • Installing CNI 🔌  ...
 ✓ Installing CNI 🔌
 • Installing StorageClass 💾  ...
 ✓ Installing StorageClass 💾
Set kubectl context to "kind-test"
You can now use your cluster with:

kubectl cluster-info --context kind-test

Have a question, bug, or feature request? Let us know! https://kind.sigs.k8s.io/#community 🙂
```

创建 Kubernetes Cluster: prod

```console
$ docker ps
CONTAINER ID   IMAGE                  COMMAND                  CREATED          STATUS          PORTS                       NAMES
91f1141a2c7f   kindest/node:v1.24.0   "/usr/local/bin/entr…"   33 seconds ago   Up 27 seconds   127.0.0.1:64501->6443/tcp   test-control-plane
c4798142e03d   kindest/node:v1.24.0   "/usr/local/bin/entr…"   3 minutes ago    Up 3 minutes    127.0.0.1:64433->6443/tcp   dev-control-plane
```

## 8. Azure 开发环境 ✅

### 8.1 安装和配置 Azure CLI ✅
- 下载 [Azure CLI](https://aka.ms/InstallAzureCliWindows) 
- 检查安装是否正确：打开 cmd 命令窗口，`az --version`
``` console
$ az --version
azure-cli                         2.37.0

core                              2.37.0
telemetry                          1.0.6

Dependencies:
msal                            1.18.0b1
azure-mgmt-resource             21.1.0b1

Python location 'C:\Program Files (x86)\Microsoft SDKs\Azure\CLI2\python.exe'
Extensions directory 'C:\Users\vmaping\.azure\cliextensions'

Python (Windows) 3.10.4 (tags/v3.10.4:9d38120, Mar 23 2022, 22:57:10) [MSC v.1929 32 bit (Intel)]

Legal docs and information: aka.ms/AzureCliLegal


Your CLI is up-to-date.

Please let us know how we are doing: https://aka.ms/azureclihats
and let us know if you're interested in trying out our newest features: https://aka.ms/CLIUXstudy
$ which az
/mnt/c/Program Files (x86)/Microsoft SDKs/Azure/CLI2/wbin/az
``` 
>说明：az 在 Windows 10 下的 cmd terminal 和 ubuntu terminal 中是同一个 az。

### 8.2 安装和配置 Azure Function CLI ✅
- [Install the Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cwindows%2Ccsharp%2Cportal%2Cbash#install-the-azure-functions-core-tools)
- 检查安装是否正确：打开 cmd 命令窗口，`func --version`
``` console
$ func --version
4.0.4544
$ where func
C:\Program Files\Microsoft\Azure Functions Core Tools\func.exe
```
>说明：func 在 Windows 10 下的 cmd terminal 和 ubuntu terminal 要分别单独安装。

## 9. AWS 开发环境

### 9.1 安装和配置 AWS CLI ✅
- 下载 [AWS CLI](https://awscli.amazonaws.com/AWSCLIV2.msi)
- 检查安装是否正确：打开 cmd 命令窗口，`aws --version`
``` console
$ aws --version
aws-cli/2.7.9 Python/3.9.11 Windows/10 exe/AMD64 prompt/off
$ where aws
C:\Program Files\Amazon\AWSCLIV2\aws.exe
``` 
>重要：建议下载 AWS CLI 2，AWS CLI 2 和 1 不兼容，新功能只增加到 AWS CLI 2 上。

### 9.2 使用 Docker 运行 AWS CLI ✅
``` console
$ docker run --rm -it amazon/aws-cli --version
Unable to find image 'amazon/aws-cli:latest' locally
latest: Pulling from amazon/aws-cli
8de5b65bd171: Pull complete
6081874c50da: Pull complete
f346e31030cb: Pull complete
cd4e94fb04e7: Pull complete
71c2536d7d65: Pull complete
Digest: sha256:c95ab2277ee36252dd31b7c50a6a3e82eb558089618bfd22308f8e0da3d753c3
Status: Downloaded newer image for amazon/aws-cli:latest
aws-cli/2.7.9 Python/3.9.11 Linux/5.10.102.1-microsoft-standard-WSL2 docker/x86_64.amzn.2 prompt/off
```

## Reference


# Windows 下开发环境设置 (2022-06-06 更新)

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
[Install Linux on Windows with WSL](：https://docs.microsoft.com/en-us/windows/wsl/install) 是安装 Docker 的前置条件。

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

要想安装其它 Linux，首先查看可以安装的 Linux 列表
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
>重要：Docker for Windows 目前只支持 Windows 10 和 Windows Server 2016，不支持 Windows 7。

- 下载 [Docker](https://docs.docker.com/docker-for-windows/install/) ，点击 Get Docker for Windows (Stable)
- 安装 Docker for Windows 10 

    - 安装过程中会提示需要开启 Hyper-V 功能，点击 OK 后，完成设置后会自动重启机器。
    ![image](./images/env-windows-10-01.png)
    - 控制面板 -> 程序 -> 程序和功能，点击"启用或关闭 Windows 功能"，勾选中 "Hyper-V"
    ![image](./images/env-windows-10-02.png)
    - 确认 Virtualization 已经开启
    ![image](./images/env-windows-10-03.png)

-	检查安装是否正确：打开 cmd 命令窗口，`docker --version`
``` console
$ docker --version
Docker version 20.10.11, build dea9396
```
-	配置容器镜像加速器 (如果你的环境下，下载 Docker 镜像速度足够快，此步可以免做)
    ![image](./images/env-windows-10-04.png)

    - https://bowubc7e.mirror.aliyuncs.com   
    - http://07ddb7e7.m.daocloud.io  
    - http://maping930883.m.alauda.cn

-	检查安装是否正确：打开 cmd 命令窗口，`docker run hello-world`
``` console
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
0e03bdcc26d7: Pull complete
Digest: sha256:e7c70bb24b462baa86c102610182e3efcb12a04854e8c582838d92970a09f323
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

### 7.3 安装 kubectl ✅
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
>说明：Docker Desktop for Windows 会在 PATH（C:\Program Files\Docker\Docker\resources\bin）中添加自己的 kubectl 程序。 如果你之前安装过 Docker Desktop，你可能需要将新安装的 PATH 项放到 Docker Desktop 安装程序所添加的目录之前，或者干脆删除 Docker Desktop 所安装的 kubectl。

>重要：因为 kubectl 是绿色安装，Windows 下 cmd terminal 和 ubuntu terminal 之间是彼此不通的。

>参考：https://kubernetes.io/zh/docs/tasks/tools/install-kubectl/

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
```  

### 8.2 安装和配置 Azure Function CLI ✅
- [Install the Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cwindows%2Ccsharp%2Cportal%2Cbash#install-the-azure-functions-core-tools)
- 检查安装是否正确：打开 cmd 命令窗口，`func --version`
``` console
$ func --version
4.0.4544
```
## 9. AWS 开发环境

## 安装 Terraform
- 下载 [Teffaform](https://www.terraform.io/downloads.html)

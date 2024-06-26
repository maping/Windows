# Windows 下开发环境设置 (2023-11-30 更新)

## 1. 一键显示环境变量窗口 ✅
1. 桌面创建快捷方式，Target 输入: rundll32.exe sysdm.cpl,EditEnvironmentVariables
2. 右键 Run as administrator，可以添加修改 System Variables

## 2. 绿色安装 Git ✅
- 下载 [Git](https://git-scm.com/download/win)，选择 64-bit Git for Windows Portable。
- 加入 PATH 环境变量：C:\Software\PortableGit\bin
-	检查安装是否正确：打开 cmd 命令窗口，输入 `git --version`
``` console
$ git --version
git version 2.43.0.windows.1
```

## 3. 安装和配置 FileZilla ✅
- 下载 [FileZilla](https://filezilla-project.org/download.php) 
>注意: 不能直接下载 .exe 文件，安全检查会报告有 virus，可以下载 FileZilla_3.60.1_win64.zip。

## 4. 安装和配置 MobaXterm ✅
- 下载 [MobaXterm](https://mobaxterm.mobatek.net/download.html) 
>说明：下载 MobaXterm_Portable_v22.0.zip

## 5. 安装和配置 WinSCP ✅
- 下载 [WinSCP 5.19.6](https://winscp.net/eng/download.php) 

## 6. Java 开发环境

### 6.1 安装和配置 Open JDK ✅
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

### 6.2 安装和配置 Ant 
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

### 6.3 安装和配置 Maven 
- 下载 [Maven](https://maven.apache.org/download.cgi)
- 解压缩：apache-maven-3.8.6-bin.zip
- 设置环境变量 M2_HOME，例如：C:\Software\apache\maven
- 设置环境变量 PATH，增加一条，%M2_HOME%\bin 
- 设置环境变量 MAVEN_OPTS，例如：-Xms512m -Xmx1024m
- 检查安装是否正确：打开 cmd 命令窗口，`mvn -version`
``` console
$ mvn -version
Picked up JAVA_TOOL_OPTIONS: -Dlog4j2.formatMsgNoLookups=true
Apache Maven 3.8.6 (84538c9988a25aec085021c365c560670ad80f63)
Maven home: C:\Software\Apache\maven
Java version: 17, vendor: Oracle Corporation, runtime: C:\Software\java\openjdk
Default locale: en_US, platform encoding: GBK
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"
```

## 7. .NET 开发环境

### 7.1 .NET Framework 开发环境 
下载并安装 Vistual Studio 2019

### 7.2 .NET Core | .NET 6 开发环境
下载并安装 Vistual Studio 2022

## 8. Python 开发环境

### 8.1 安装多版本的 Python ✅
- 下载 [Python](https://www.python.org)
- 安装 Python 3.12
  - 双击安装：python-3.12.0-amd64.exe
    - 选择 Customize installation
    - 勾选 Add python.exe to PATH
    - 勾选 Install Python 3.12 for all users
    - Customize install location: C:\Users\vmaping\AppData\Local\Programs\Python\Python312 
  - 修改 python.exe 为 python312.exe
  - 设置环境变量 PATH
    - C:\Users\vmaping\AppData\Local\Programs\Python\Python312\Scripts\
    - C:\Users\vmaping\AppData\Local\Programs\Python\Python312\
  - 检查安装是否正确：打开一个 cmd 窗口，输入 `python312`
  ``` console
  $ python312
  Python 3.12.0 (tags/v3.12.0:0fb18b0, Oct  2 2023, 13:03:39) [MSC v.1935 64 bit (AMD64)] on win32
  Type "help", "copyright", "credits" or "license" for more information.
  >>>
  ```
- 安装 Python 3.11
  - 双击安装：python-3.11.6-amd64.exe
    - 选择 Customize installation
    - 勾选 Add python.exe to PATH
    - 勾选 Install Python 3.11 for all users
    - Customize install location: C:\Users\vmaping\AppData\Local\Programs\Python\Python311 
  - 修改 python.exe 为 python311.exe
  - 设置环境变量 PATH
    - C:\Users\vmaping\AppData\Local\Programs\Python\Python311\Scripts\
    - C:\Users\vmaping\AppData\Local\Programs\Python\Python311\
  - 检查安装是否正确：打开一个 cmd 窗口，输入 `python311`
  ``` console
  $ python311
  Python 3.11.6 (tags/v3.11.6:8b6ee5b, Oct  2 2023, 14:57:12) [MSC v.1935 64 bit (AMD64)] on win32
  Type "help", "copyright", "credits" or "license" for more information.
  >>>
  ```

### 8.2 为 VSCode 配置 Python 开发运行环境
- 常用插件安装
  - 安装 Microsoft 出品的 Python 插件
  - 安装 Cstrap 出品的 python-snippets 插件
    - 输入 def，自动输出函数定义框架，按 Tab 键切换到每个项 
- 修改配置
  - 设置默认的 terminal 为 cmd
    - 点击右下角的 + 下拉列表，选择 Select Default Profile，选择 Command Prompt
    - 右键 .py 文件，选择 Run Python -> Run Python File in Python Terminal，确认出现的 cmd terminal
  - 括号自动补全
    - 修改配置文件：Settings -> Text Editor -> Edit in settings.json
      - "python.analysis.completeFunctionParens": true,
    - 输入 print，自动出现（），并且光标在括号中
- 虚拟环境
   - 全局模块
     - 运行 pip install <模块> 时，会在 pip 所对应的 Python 的解释器下的 Lib\site-packages 目录下安装该模块
     - 所有的 Python 程序共用这些模块
     - 同一个模块只能安装一个版本，无法满足不同 Python 程序对同一模块不同版本的要求
   - 每个项目通过虚拟环境自己管理自己的 Python 环境（解释器和模块）
   - 在 monthly-report 目录下执行 `python312 -m venv .venv`
     - 此时 VSCode 会报告无法找到 Python 解析器，因为已经修改了 Python 3.12 的默认 python.exe 为 python312.exe，所以找不到了
     - 点击 find，指定 .venv 目录下的 .venv\Scripts\python312.exe，此时右下角的的 Python 解释器变为了当前项目目录下的 .venv
     - 在 VSCode 中打开一个虚拟环境终端（注意，不能打开系统的 cmd terminal）
       - (.venv) C:\Code\python-projects\monthly-report> pip install pandas
       - (.venv) C:\Code\python-projects\monthly-report> pip install numpy
       - (.venv) C:\Code\python-projects\monthly-report> pip install openpyxl
     - 右键 main.py，Run Python -> Run Python File in Terminal，可以在虚拟环境下成功运行了！
  - 在 sms-pricing 目录下执行 `python312 -m venv .venv`
     - 点击 find，指定 .venv 目录下的 .venv\Scripts\python312.exe，此时右下角的的 Python 解释器变为了当前项目目录下的 .venv
     - 在 VSCode 中打开一个虚拟环境终端（注意，不能打开系统的 cmd terminal）
       - (.venv) C:\Code\python-projects\sms-pricing> pip install requests
       - (.venv) C:\Code\python-projects\sms-pricing> pip install bs4
       - (.venv) C:\Code\python-projects\sms-pricing> pip install pandas
       - (.venv) C:\Code\python-projects\sms-pricing> pip install numpy
       - (.venv) C:\Code\python-projects\sms-pricing> pip install openpyxl
     - 右键 main.py，Run Python -> Run Python File in Terminal，TODO 有问题，待查！
   - 在 huggingface 目录下执行 `python311 -m venv .venv`
     - 点击 find，指定 .venv 目录下的 .venv\Scripts\python311.exe，此时右下角的的 Python 解释器变为了当前项目目录下的 .venv
     - 在 VSCode 中打开一个虚拟环境终端（注意，不能打开系统的 cmd terminal）
       - (.venv) C:\Code\python-projects\huggingface> pip install transformers
       - (.venv) C:\Code\python-projects\huggingface> pip install datasets
       - (.venv) C:\Code\python-projects\huggingface> pip install torch torchvision torchaudio
       - (.venv) C:\Code\python-projects\huggingface> python311.exe -m pip install --upgrade pip
     - 右键 .py，Run Python -> Run Python File in Terminal，可以在虚拟环境下成功运行了！

### 8.3 安装 [Pytorch](https://pytorch.org/get-started/locally/)
由于 Pytorch 目前最高只支持 Python 3.11，所以这里只能用 Python 3.11。
```console
$ pip3.11 install torch torchvision torchaudio
```

参考：[【最新教程】5分钟搞定VScode中配置Python运行环境](https://www.bilibili.com/video/BV1TN411K7sn/)
 
## 9. Node.JS 开发环境

### 9.1 安装和配置 NodeJS ✅
- 下载 [Node.JS](https://nodejs.org)，选择 LTS
- 双击安装：node-v20.9.0-x64.msi
- 设置环境变量 PATH
- 检查安装是否正确：打开一个 cmd 窗口
``` console
$ npm -v
10.1.0
$ npm install -g npm@10.2.1
$ npm -v
10.2.1
$ node -v
v20.9.0
$ npm install -g yarn
$ yarn -v
1.22.19
```
### 9.2 为 VSCode 配置 Node.JS 开发运行环境

## 10. 容器开发环境 ✅

### 10.1 Install Linux on Windows with WSL
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

### 10.2 安装和配置 Docker Desktop ✅
>重要：Docker for Windows 目前只支持在服务支持期内的 Windows 10 。

- 下载 [Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/install/) 
- 双击 Docker Desktop Installer.exe 开始安装，安装过程保持默认选项即可
- 检查安装是否正确：打开 cmd 命令窗口，`docker --version`
``` console
$ docker --version
Docker version 24.0.6, build ed223bc
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

Docker Desktop 自带 Kubernetes，勾选 Kubernetes -> Enable Kubernetes，Apply & Restart
```console
$ kubectl get nodes
NAME             STATUS   ROLES           AGE     VERSION
docker-desktop   Ready    control-plane   2m57s   v1.24.0
```
>说明：Enable Kubernetes 后，会发现有一个单节点的 Kubernetes Cluster。

>重要：感觉没有 Kind 好用，还是不要 Enable 了。

### 10.3 安装 kubectl ✅

#### 10.3.1 Docker 自带的 kubectl
Docker Desktop for Windows 本身自带 kubectl
```console
$ where kubectl
C:\Program Files\Docker\Docker\resources\bin\kubectl.exe
$ cd C:\Program Files\Docker\Docker\resources\bin
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
#### 10.3.2 单独下载并安装 kubectl
- [Install kubectl binary with curl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)
- 查看 kubectl 最新稳定版: https://storage.googleapis.com/kubernetes-release/release/stable.txt 
- 科学下载 kubectl
    - https://storage.googleapis.com/kubernetes-release/release/VERSION-TAG/bin/OS/ARCH/kubectl.exe 
    - 比如：curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.30.1/bin/windows/amd64/kubectl.exe
    - VERSION-TAG 取值为版本号，比如：v1.30.1
    - OS 取值可以为 darwin, linux, windows
    - ARCH 取值可以为 386, amd64
- 设置环境变量 PATH，增加一条，C:\Software\Google\Kubernetes
- 检查安装是否正确：打开 cmd 命令窗口，`kubectl version --client -o yaml`
>重要：请把手工安装的 kubectl 的 PATH 项放到 Docker Desktop 安装程序所添加的目录之前。
```console
$ kubectl version --client -o yaml
clientVersion:
  buildDate: "2024-05-14T10:50:53Z"
  compiler: gc
  gitCommit: 6911225c3f747e1cd9d109c305436d08b668f086
  gitTreeState: clean
  gitVersion: v1.30.1
  goVersion: go1.22.2
  major: "1"
  minor: "30"
  platform: windows/amd64
kustomizeVersion: v5.0.4-0.20230601165947-6ce0bf390ce3
```

### 10.4 安装 [K9S](https://k9scli.io/)
```console
$ k9s version
 ____  __.________
|    |/ _/   __   \______
|      < \____    /  ___/
|    |  \   /    /\___ \
|____|__ \ /____//____  >
        \/            \/

Version:    v0.28.2
Commit:     694159b857314de5b69f251e42a5931f32105cb8
Date:       2023-11-12T06:19:03Z
```

### 10.5 安装 kind
直接下载 [kind-windows-amd64](https://github.com/kubernetes-sigs/kind)，改名为 kind.exe，放到 PATH 路径下。
```console
$ kind version
kind v0.20.0 go1.20.4 windows/amd64
```

## 11. Azure 开发环境 ✅

### 11.1 安装和配置 Azure CLI ✅
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

### 11.2 安装和配置 Azure Function CLI ✅
- [Install the Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cwindows%2Ccsharp%2Cportal%2Cbash#install-the-azure-functions-core-tools)
- 检查安装是否正确：打开 cmd 命令窗口，`func --version`
``` console
$ func --version
4.0.4544
$ where func
C:\Program Files\Microsoft\Azure Functions Core Tools\func.exe
```
>说明：func 在 Windows 10 下的 cmd terminal 和 ubuntu terminal 要分别单独安装。

## 12. AWS 开发环境

### 12.1 安装和配置 AWS CLI ✅
- 下载 [AWS CLI](https://awscli.amazonaws.com/AWSCLIV2.msi)
- 检查安装是否正确：打开 cmd 命令窗口，`aws --version`
``` console
$ aws --version
aws-cli/2.16.4 Python/3.11.8 Windows/10 exe/AMD64
$ where aws
C:\Program Files\Amazon\AWSCLIV2\aws.exe
``` 
>重要：建议下载 AWS CLI 2，AWS CLI 2 和 1 不兼容，新功能只增加到 AWS CLI 2 上。

### 12.2 使用 Docker 运行 AWS CLI ✅
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
### 12.3 安装并配置  [eksctl](https://eksctl.io/)
```console
$ eksctl version
0.182.0
```
### 12.4 安装并配置 [eks-node-viewer](https://github.com/awslabs/eks-node-viewer)
```console
$ eks-node-viewer --version
eks-node-viewer version 0.6.0
commit: e45ef3df0d6efbf25693f7d16c103593f8a3c006
built at: 2023-11-28T17:30:17Z
built by: goreleaser
```

## 13. 绿色安装 VSCode 安装和配置

### 13.1 [下载并安装](https://code.visualstudio.com/download)

### 13.2 通用配置
- 设置字体固定大小：Settings -> Text Editor -> Font: Font Size
- 按鼠标滚轮缩放字体大小
  - 修改配置文件：Settings -> Text Editor -> Edit in settings.json
    - "editor.mouseWheelZoom": true,


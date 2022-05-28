# Windows 下开发环境设置

## 1. 安装和配置 Open JDK
- 下载 [Open JDK](https://openjdk.java.net/)
- 解压缩：openjdk-17_windows-x64_bin.zip
- 设置环境变量 JAVA_HOME，例如：C:\software\java\openjdk
- 设置环境变量 PATH，增加一条，%JAVA_HOME%\bin
- 检查安装是否正确：打开一个 cmd 窗口，输入 `java -version`

``` console
$ java -version
openjdk 17 2021-09-14
OpenJDK Runtime Environment (build 17+35-2724)
OpenJDK 64-Bit Server VM (build 17+35-2724, mixed mode, sharing)
```

## 安装 Git
- 下载 [Git](https://git-scm.com/download/win) 
-	检查安装是否正确：打开 cmd 命令窗口，输入 `git --version`
``` console
$ git --version
git version 2.32.0.windows.1
```
## 安装和配置 Ant
- 下载 [Ant](https://ant.apache.org/bindownload.cgi)
- 解压缩：apache-ant-1.10.10-bin.zip
- 设置环境变量 ANT_HOME，例如：C:\software\apache\ant
- 设置环境变量 PATH，增加一条，%ANT_HOME%\bin
- 检查安装是否正确：打开一个 cmd 窗口，输入 `ant -version`
``` console
$ ant -version
Apache Ant(TM) version 1.10.10 compiled on April 12 2021
```

## 安装和配置 Maven
- 下载 [Maven](https://maven.apache.org/download.cgi)
- 解压缩：apache-maven-3.8.2-bin.zip
-	设置环境变量 M2_HOME，例如：C:\software\apache\maven
- 设置环境变量 PATH，增加一条，%M2_HOME%\bin 
- 设置环境变量 MAVEN_OPTS，例如：-Xms512m -Xmx1024m
- 检查安装是否正确：打开 cmd 命令窗口，`mvn -version`
``` console
$ mvn -version
Apache Maven 3.8.2 (ea98e05a04480131370aa0c110b8c54cf726c06f)
Maven home: C:\software\apache\maven
Java version: 17, vendor: Oracle Corporation, runtime: C:\software\java\openjdk
Default locale: en_US, platform encoding: GBK
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"
```

## 安装和配置 FileZilla
- 下载 [FileZilla](https://filezilla-project.org/download.php) 
>注意: 不能直接下载 .exe 文件，安全检查会报告有 virus，不让下载。

## 安装和配置 Nexus 3 
- 下载 [Nexus 3](https://www.sonatype.com/nexus-repository-oss) 

## 安装和配置 MobaXterm
- 下载 [MobaXterm](https://mobaxterm.mobatek.net/download.html) 

## 安装和配置 WinSCP
- 下载 [WinSCP](https://winscp.net/eng/download.php) 
 
## 安装和配置 Docker 
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

## 安装 kubectl 
-	查看 kubectl 最新稳定版: https://storage.googleapis.com/kubernetes-release/release/stable.txt 
- 科学下载 kubectl：https://storage.googleapis.com/kubernetes-release/release/VERSION-TAG/bin/OS/ARCH/kubectl.exe ，比如：- 下载 curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.23.4/bin/windows/amd64/kubectl.exe
    - VERSION-TAG 取值为版本号，比如：v1.23.4
    - OS 取值可以为 darwin, linux, windows
    - ARCH 取值可以为 386, amd64
-	设置环境变量 PATH，增加一条，C:\software\google\kubernetes 
- 检查安装是否正确：打开 cmd 命令窗口，```kubectl version```
```console
$ kubectl version --client
Client Version: version.Info{Major:"1", Minor:"23", GitVersion:"v1.23.4", GitCommit:"e6c093d87ea4cbb530a7b2ae91e54c0842d8308a", GitTreeState:"clean", BuildDate:"2022-02-16T12:38:05Z", GoVersion:"go1.17.7", Compiler:"gc", Platform:"windows/amd64"}
$ kubectl version
Client Version: version.Info{Major:"1", Minor:"21", GitVersion:"v1.21.2", GitCommit:"092fbfbf53427de67cac1e9fa54aaa09a28371d7", GitTreeState:"clean", BuildDate:"2021-06-16T12:59:11Z", GoVersion:"go1.16.5", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.7", GitCommit:"6b3f9b283463c1d5a2455df301182805e65c7145", GitTreeState:"clean", BuildDate:"2021-05-19T22:28:47Z", GoVersion:"go1.15.12", Compiler:"gc", Platform:"linux/amd64"}
```
>说明：Docker Desktop for Windows 会在 PATH（C:\Program Files\Docker\Docker\resources\bin）中添加自己的 kubectl 程序。 如果你之前安装过 Docker Desktop，你可能需要将新安装的 PATH 项放到 Docker Desktop 安装程序所添加的目录之前，或者干脆删除 Docker Desktop 所安装的 kubectl。

>参考：https://kubernetes.io/zh/docs/tasks/tools/install-kubectl/

## 安装和配置 Azure CLI
- 下载 [Azure CLI](https://aka.ms/InstallAzureCliWindows) 
- 检查安装是否正确：打开 cmd 命令窗口，`az --version`
``` console
$ az --version
azure-cli                         2.35.0

core                              2.35.0
telemetry                          1.0.6

Extensions:
azure-firewall                    0.12.0
containerapp                       0.2.2
log-analytics                      0.2.2
spring-cloud                      2.10.0

Dependencies:
msal                              1.17.0
azure-mgmt-resource               20.0.0

Python location 'C:\Program Files (x86)\Microsoft SDKs\Azure\CLI2\python.exe'
Extensions directory 'C:\Users\pinm\.azure\cliextensions'

Python (Windows) 3.10.3 (tags/v3.10.3:a342a49, Mar 16 2022, 12:53:06) [MSC v.1929 32 bit (Intel)]

Legal docs and information: aka.ms/AzureCliLegal


Your CLI is up-to-date.

Please let us know how we are doing: https://aka.ms/azureclihats
and let us know if you're interested in trying out our newest features: https://aka.ms/CLIUXstudy
```  

## 安装 SQuirrel
- 下载 [SQuirrel](http://www.squirrelsql.org/#installation)
- 安装：以管理员身份打开一个 cmd 窗口，执行 ```java -jar squirrel-sql-3.8.1-standard.jar```

## 安装 MySQL Connector
- 下载 [MySQL Connector](https://dev.mysql.com/downloads/connector/j/)

## 安装 Terraform
- 下载 [Teffaform](https://www.terraform.io/downloads.html)


# Windows 下 Netbeans 开发环境设置

## 1. 安装 Netbeans
- 下载 [Netbeans](https://netbeans.apache.org/) ，选择 netbeans-15-bin.zip 绿色安装版
- 解压缩

## 2. 启动 Netbeans
启动前需要配置 JDK，打开 etc/netbeans.conf，找到 netbeans_jdkhome 这行，指向本机的 JDK
```code
netbeans_jdkhome="C:\Software\Java\openjdk\"
```
>重要：这里使用了 OpenJDK 11，如果使用高版本的 JDK，会导致项目构建失败。

双击 bin\netbeans64.exe 启动，允许 Windows Firewall 启动 Tomcat

## 3. 配置 Maven
Tools->Options->Java->Maven，Maven Home 指向本机的 Maven 安装目录。
>【最佳实践】不要用 Netbeans 自带的 Maven，而是使用本机安装的 Maven。

## 4. 添加 Tomcat Server
Services->Servers，右键 Add Server...，选择 Apache Tomcat，修改名称为 Tomcat 10，
- Server Location: C:\Software\Apache\tomcat
- Username: maping
- Password: maping
>说明：添加成功后，应该会显示 Tomcat 10 上部署的应用列表。

## 5. 创建一个 Web 项目
New Project...-> Java with Maven -> Web Application，输入项目信息
- Server: Tomcat 10
- Java EE Version: Java EE 7 Web（这也是默认选项）

右键刚创建好的项目，Clean and Build，确认 BUILD SUCCESS。

右键刚创建好的项目，RUN，会自动把项目发布到 Tomcat 10 上，并打开一个浏览器显示主页。

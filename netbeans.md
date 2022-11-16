# Windows 下 Netbeans 开发环境设置

## 1. 安装 Netbeans
- 下载 [Netbeans](https://netbeans.apache.org/) ，选择 netbeans-15-bin.zip 绿色安装版
- 解压缩

## 2. 启动 Netbeans
启动前需要配置 JDK，打开 etc/netbeans.conf，找到 netbeans_jdkhome 这行，指向本机的 JDK
```code
netbeans_jdkhome="C:\Software\Java\openjdk\"
```
双击 bin\netbeans64.exe 启动

## 3. 配置 Maven
【最佳实践】不要用 Netbeans 自带的 Maven，而是使用本机安装的 Maven。

Tools->Options->Java->Maven，Maven Home 指向本机的 Maven 安装目录。

## 4. 添加 Tomcat Server
Services->Servers，右键 Add Server...，选择 Apache Tomcat，修改名称为 Tomcat 10，
- Server Location: C:\Software\Apache\tomcat
- Username: maping
- Password: maping
添加成功后，会显示 Tomcat 10 上部署的应用列表。

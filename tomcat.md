# Windows 下 Tomcat 开发环境设置

## 1. 安装 Tomcat
- 下载 [Tomcat](https://tomcat.apache.org/index.html) ，选择 apache-tomcat-10.1.2-windows-x64.zip 绿色安装版
- 解压缩

## 2. 启动 Tomcat
Tomcat 默认启动端口是 8080，配置在 conf/server.xml 中
```code
    <Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
```
配置管理员权限，修改 conf/tomcat-users.xml 文件，增加以下内容：
```code
<role rolename="manager-gui"/>
<role rolename="manager-status"/>
<role rolename="manager-script"/>
<user username="maping" password="maping" roles="admin-gui, manager-gui, manager-jmx, mananger-status, manager-script"/>
```

启动，进入 bin，执行 startup，会弹出两个 cmd terminal console，一个是命令行环境变量输出，一个是 Server 启动输出
```console
$ startup
Using CATALINA_BASE:   "C:\Software\Apache\tomcat"
Using CATALINA_HOME:   "C:\Software\Apache\tomcat"
Using CATALINA_TMPDIR: "C:\Software\Apache\tomcat\temp"
Using JRE_HOME:        "C:\Software\java\openjdk"
Using CLASSPATH:       "C:\Software\Apache\tomcat\bin\bootstrap.jar;C:\Software\Apache\tomcat\bin\tomcat-juli.jar"
Using CATALINA_OPTS:   ""
```
注：也可以使用 `catalina.sh start` 启动，`catalina.sh stop` 停止

## 3. 目录浏览
如果想 enable directory browsing，可以修改 conf/web.xml 文件，把 listings 的 value 改为 true
```code
   <servlet>
        <servlet-name>default</servlet-name>
        <servlet-class>org.apache.catalina.servlets.DefaultServlet</servlet-class>
        <init-param>
            <param-name>debug</param-name>
            <param-value>0</param-value>
        </init-param>
        <init-param>
            <param-name>listings</param-name>
            <param-value>false</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>
```

## 4. 自动加载
默认是否自动加载？

## 参考
- [How to Install Apache Tomcat on Windows](https://phoenixnap.com/kb/install-tomcat-windows)

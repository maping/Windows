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
如果想 enable directory browsing，可以修改 conf/web.xml 文件，把 file in the conf directory and edit the file with a text editor. Directory browsing helps when testing the system, and sometimes it may be the solution for a 403 forbidden error.
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

## 3. 配置 Maven
【最佳实践】不要用 Netbeans 自带的 Maven，而是使用本机安装的 Maven。

Tools->Options->Java->Maven，Maven Home 指向本机的 Maven 安装目录。



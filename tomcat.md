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
&lt;servlet&gt;
  &lt;servlet-name&gt;default&lt;/servlet-name&gt;
  &lt;servlet-class&gt;org.apache.catalina.servlets.DefaultServlet&lt;/servlet-class&gt;
  &lt;init-param&gt;
    &lt;param-name&gt;debug&lt;/param-name&gt;
    &lt;param-value&gt;0&lt;/param-value&gt;
  &lt;/init-param&gt;
  &lt;init-param&gt;
    &lt;param-name&gt;listings&lt;/param-name&gt;
    &lt;param-value&gt;false&lt;/param-value&gt;
  &lt;/init-param&gt;
  &lt;load-on-startup&gt;1&lt;/load-on-startup&gt;
&lt;/servlet&gt;
```

## 3. 配置 Maven
【最佳实践】不要用 Netbeans 自带的 Maven，而是使用本机安装的 Maven。

Tools->Options->Java->Maven，Maven Home 指向本机的 Maven 安装目录。



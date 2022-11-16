# Windows 下 Nexus 开发环境设置

## 1. 安装 Nexus
- 下载 [Nexus Repository OSS](https://www.sonatype.com/products/nexus-repository) ，拉到页面最下面，找到“Get Repository OSS - The Free Artifact Repository with Universal Format Support.”，点击后，注册邮箱后下载。
- 选择 nexus-3.43.0-01-win64.zip 绿色安装版
- 解压缩后有两个目录
  - nexus-3.43.0-01：包含了启动 Nexus 所需要的文件，如启动脚本，依赖 jar 包等等。
  - sonatype-work：该目录包含了 Nexus 生成的配置文件、日志文件、仓库文件。

## 2. 启动 Nexus
进入 bin 目录
- 前台启动 Nexus：nexus /run

Nexus 默认启动端口是 8081，配置在 /etc/nexus-default.properties 中
```code
## DO NOT EDIT - CUSTOMIZATIONS BELONG IN $data-dir/etc/nexus.properties
##
# Jetty section
application-port=8081
application-host=0.0.0.0
nexus-args=${jetty.etc}/jetty.xml,${jetty.etc}/jetty-http.xml,${jetty.etc}/jetty-requestlog.xml
nexus-context-path=/

# Nexus section
nexus-edition=nexus-pro-edition
nexus-features=\
 nexus-pro-feature

nexus.hazelcast.discovery.isEnabled=true
```
>【最佳实践】：如果要修改端口，不要直接修改这个文件，而是修改文件 sonatype-work\nexus3\etc\nexus.properties 中的内容

访问 http://localhost:80801 管理员账户是 admin，管理员的初始密码在 sonatype-work\nexus3\admin.password 中，首次登录后，需要修改管理员密码。
- 管理员账户口令：admin/admin123
- 是否允许匿名访问：允许
- 是否允许识别 CVE-2021-44228 (also known as "log4shell") 漏洞：允许


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

## 4. 自动加载 Web App
默认已经自动加载 Web App。

## 参考
- [How to Install Apache Tomcat on Windows](https://phoenixnap.com/kb/install-tomcat-windows)

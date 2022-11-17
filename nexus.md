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
- 管理员账户口令：admin/nexus123
- 是否允许匿名访问：允许
- 是否允许识别 CVE-2021-44228 (also known as "log4shell") 漏洞：允许

## 3. 远程仓库
- Maven 中央仓库：https://repo1.maven.org/maven2/
- Java.net 仓库：https://maven.java.net/content/groups/public/
- JBoss 仓库：https://repository.jboss.org/maven2/

## 4. 创建项目仓库
- 创建 Hosted 类型仓库
  - 创建 maven-account-release 仓库
  - 创建 maven-account-snapshot 仓库
  - 创建 maven-3rd-party 仓库
- 创建 Proxy 类型仓库
  - 创建 maven-jboss-release 仓库
  - 创建 maven-javanet-release 仓库

## 5. 为本机配置 settings.xml
把 M2_HOME/conf/settings.xml 附件复制到 ~/.m2/ 目录下，然后把 Nexus 配置为“私服+镜像”。

增加 mirror 配置
```code
  <mirror>
      <id>nexus</id>
      <mirrorOf>external:http:*</mirrorOf>
      <url>http://localhost:8081/repository/maven-public/</url>
  </mirror>
```

## 参考
- [nexus 3.2 and sonatype installation, admin login and port change](https://www.youtube.com/watch?v=A8nAPgoI2hY)
- [Complete Sonatype Nexus Tutorial Beginner to Advanced Part#1 of 5](https://www.youtube.com/watch?v=_tn1dDmxiBw)
- [Complete Sonatype Nexus Tutorial Beginner to Advanced Part#2 of 5]()
- [Complete Sonatype Nexus Tutorial Beginner to Advanced Part#3 of 5]()
- [Complete Sonatype Nexus Tutorial Beginner to Advanced Part#4 of 5]()
- [Complete Sonatype Nexus Tutorial Beginner to Advanced Part#5 of 5]()



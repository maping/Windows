# CMD Terminal

## 1. 常用快捷键
- 半透明窗口
- 查看历史命令: F7
- 切换全屏: Alt + 回车 
- 鼠标右键粘贴剪贴板内容

但是不支持跨行命令
	5. 从 explorer 快速进入 cmd
	6. 查看命令的位置: where
	7. 删除目录：rd /s/q 目录路径
	

##  2. 解决 cmd 窗口中文字符乱码问题
- 查看 cmd 窗口字符编码: chcp 
- 修改 cmd 窗口字符编码: chcp <字符编码>
- 字符编码对应代码:
	- 65001——UTF-8
	- 936——简体中文
	- 950——繁体中文
	- 437——美国/加拿大英语
	- 932——日文
	- 949——韩文
	- 866——俄文

# 开机自启动应用程序
    把应用程序的快捷方式放到 C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp 目录下
# 管理开机自启动项
    按下 Win + R ，输入 msconfig，点击 Startup，Open Task Manager
# 查看机器 Serial Number
    打开 PowerShell 窗口，运行：gwmi –class win32_bios

# 如何查看端口占用的程序
netstat -aon|findstr "8009"

tasklist|findstr "78796"

wmic process 78796 get commandline


wmic process where caption="java.exe" get caption,commandline /value

参考文献：
	1. https://www.cnblogs.com/top5/p/3143837.html

# 查看 CPU Core 
    按下 Win + X ，选择 Device Manager，点击 Processors
    

 
   打开 Task Manager，右键 CPU Graph，选择 Change Graph to -> Logical Processors


# jar 命令可以处理 .jar、.war、.ear 类型的压缩文件
	1. 创建压缩文件：jar -cvf 目标压缩文件 压缩目录/文件（多个目录/文件之间以空格间隔）（1）jar -cvf ehcache.war META-INF/ WEB-INF/
	2. 查看压缩文件：jar -tvf 压缩文件
	（1）jar -tvf ehcache.war 
	3. 解压压缩文件：jar -xvf 压缩文件
	（1）
	
![image](https://user-images.githubusercontent.com/7236807/170800891-1be7a03c-e98d-402b-8cea-29dc967ad6af.png)

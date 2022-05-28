# CMD Terminal

## 1. 常用快捷键
- 半透明窗口
- 查看历史命令: F7
- 切换全屏/还原: Alt + 回车 
- 鼠标右键粘贴剪贴板内容
>注意：cmd terminal 不支持跨行命令。
	
## 2. 查看命令的位置
```console
where python
```

## 3. 文件命令

### 3.1 查看文件内容
```console
type python
```
### 3.2 创建文件
```console
echo hello > hello.md
```
### 3.3 修改文件名
```console
move hello.md helloworld.md
```
### 3.4 删除文件
```console
del helloworld.md
```

## 4. 目录命令

### 4.1 创建目录

### 4.1 修改目录名

### 4.1 删除目录
rd /s/q 目录路径

### 4.1 复制目录


## 4. 解决 cmd 窗口中文字符乱码问题
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

## 5. 查看占用指定端口的程序
```console
netstat -aon|findstr "8009"
```

```console
tasklist|findstr "78796"
```

```console
wmic process 78796 get commandline
```

```console
wmic process where caption="java.exe" get caption,commandline /value
```

## 6. 查看 CPU Core 
1. 按下 Win + X ，选择 Device Manager，点击 Processors
2. 打开 Task Manager，右键 CPU Graph，选择 Change Graph to -> Logical Processors

## 7. jar 命令可以处理 .jar、.war、.ear 类型的压缩文件
1. 创建压缩文件：jar -cvf 目标压缩文件 压缩目录/文件（多个目录/文件之间以空格间隔）
- jar -cvf ehcache.war META-INF/ WEB-INF/
2. 查看压缩文件：jar -tvf 压缩文件
- jar -tvf ehcache.war 
3. 解压压缩文件：jar -xvf 压缩文件
	
## Reference
- [比CMD更强大的命令行WMIC](https://www.cnblogs.com/top5/p/3143837.html)

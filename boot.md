# Windows Boot Loader

## 1. 查看当前开机的启动菜单项

以系统管理员身份打开一个 cmd
```console
C:\WINDOWS\system32>bcdedit /enum all
```

## 2. 修改开机启动菜单项
修改前，先把当前的启动菜单项备份
```console
C:\WINDOWS\system32>bcdedit /export C:\Users\pinm\bcd.bak
```

增加开机启动的菜单项
```console
C:\WINDOWS\system32>bcdedit /copy {current} /d "No Hyper-V"
The entry was successfully copied to {79e3b6d0-bea5-11e7-8101-f29f4a0ab42f}.
C:\WINDOWS\system32>bcdedit /set {79e3b6d0-bea5-11e7-8101-f29f4a0ab42f} hypervisorlaunchtype off
The operation completed successfully.
```
重启机器，将会看到增加了 "No Hyper-V" 这一启动菜单项


## 3. 删除开机启动的菜单项
```code
Windows Boot Loader
-------------------
identifier              {79e3b6d0-bea5-11e7-8101-f29f4a0ab42f}
device                  partition=C:
path                    \WINDOWS\system32\winload.efi
description             No Hyper-V
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {79e3b6ce-bea5-11e7-8101-f29f4a0ab42f}
displaymessageoverride  Recovery
recoveryenabled         Yes
badmemoryaccess         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \WINDOWS
resumeobject            {de64c486-91ca-11e7-a311-54ee75dc9efe}
nx                      OptIn
bootmenupolicy          Standard
hypervisorlaunchtype    Off           {79e3b6d0-bea5-11e7-8101-f29f4a0ab42f}
device                  partition=C:
path                    \WINDOWS\system32\winload.efi
description             No Hyper-V
```

```console
bcdedit /delete {79e3b6d0-bea5-11e7-8101-f29f4a0ab42f}
bcdedit /deletevalue {79e3b6d0-bea5-11e7-8101-f29f4a0ab42f} hypervisorlaunchtype
```

点击 Delete 将其删除

以系统管理员身份打开一个 cmd，运行 msconfig，点击Boot

选择你要删除的菜单项

点击 Delete ，发现提示

## 4. 开机自启动应用程序
把应用程序的快捷方式放到 C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp 目录下

## 5. 管理开机自启动项
按下 Win + R ，输入 msconfig，点击 Startup，Open Task Manager

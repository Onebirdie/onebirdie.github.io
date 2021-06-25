---
title: Shell
date: 2021-06-25
---
# Shell



**source filename 和 sh filename 及./filename执行脚本的区别**

```tex
1. 当shell脚本具有可执行权限时，用sh filename与./filename执行脚本是没有区别得。./filename是因为当前目录没有在PATH中，所有”.”是用来表示当前目录的。
2. sh filename 重新建立一个子shell，在子shell中执行脚本里面的语句，该子shell继承父shell的环境变量，但子shell新建的、改变的变量不会被带回父shell。
3. source filename：这个命令其实只是简单地读取脚本里面的语句依次在当前shell里面执行，没有建立新的子shell。那么脚本里面所有新建、改变变量的语句都会保存在当前shell里面。
```



**文件描述符和文件句柄**

```tex
1. 内核对所有打开的文件维护有一个系统级的描述表格(open file description table)。并将表中各条目称为打开文件句柄(open file handle) 
2. 文件描述符是一个整数。代表fdtable中的索引位置（下标），指向具体的struct file（文件句柄）
```



**/dev/null**

```tex
/dev/null（或称空设备）在类Unix系统中是一个特殊的设备文件，它丢弃一切写入其中的数据（但报告写入操作成功），读取它则会立即得到一个EOF。
在程序员行话，尤其是Unix行话中，/dev/null被称为比特桶或者黑洞。
```


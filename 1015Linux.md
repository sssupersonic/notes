## Linux

这周在学redis和mongodb的时候又复习并学习了一些linux的相关知识。

### VMwareTools

卸载重装以得到最新版本的vmtools。

1.先卸载相关软件

```
sudo vmware-uninstall-tools.pl
sudo apt-get purge open-vm-tools open-vm-tools-desktop
```

2.安装

```
sudo apt-get update
sudo apt-get install open-vm-tools-desktop
```

### 防火墙

在使用resp时需要更改虚拟机的防火墙设置。使用firewall-cmd --zone=public --list-ports 查询开放了哪些防火墙端口，这时linux会提示下载相关文件。下载好以后编辑防火墙配置文件。详情见csdn

[https://blog.csdn.net/Bilal_0/article/details/126083926?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522169735316516800188582856%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&amp;request_id=169735316516800188582856&amp;biz_id=0&amp;utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-126083926-null-null.142^v96^control&amp;utm_term=resp%E6%97%A0%E6%B3%95%E8%BF%9E%E6%8E%A5redis%E6%9C%8D%E5%8A%A1%E5%99%A8&amp;spm=1018.2226.3001.4187]: 

###  常用指令

- **ls**：列出目录内容
- **cd**：切换目录
- **mkdir**：创建目录
- **rm**：删除文件或目录
- **touch**：创建空文件
- **cat**：连接文件并显示内容
- **grep**：在文件中搜索文本模式
- **vi** 或 **nano**：文本编辑器
- **ps**：列出当前运行进程
- **kill**：结束进程

### 权限

Linux 使用一种基于权限的安全模型。基本权限分为读（r）、写（w）、执行（x）三种，分别对应不同的用户：所有者、所属组、其他用户。命令前加sudo基本能解决大多数权限问题，但有一些需要su进root。其他操作有chmod、chown、chgrp。
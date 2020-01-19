# Linux探索之旅
## 一、Ubuntu环境搭建
> 配置：UEFI新式BIOS，128G SSD + 1T 机械硬盘，win10+Ubuntu，DELL G7 7588


## 二、Ubuntu更换下载源
1. 将源文件备份  
目录`/etc/apt/`下有文件`sources.list`，是包管理工具apt所用的记录软件包仓库位置的配置文件。用命令：

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

2. 查看新版本信息

查询自己Ubuntu版本的系统代号。例如：

> Ubuntu 18.04 系统代号为bionic  
> Ubuntu 12.04 (LTS)代号为precise  
> Ubuntu 14.04 (LTS)代号为trusty  
> Ubuntu 15.04 代号为vivid  
> Ubuntu 15.10 代号为wily  
> Ubuntu 16.04 (LTS)代号为xenial

用命令：
```
lsb_release -c
```

3. 编辑源列表文件

首先安装vim编辑器，然后打开文件进行编辑。命令：
```
sudo apt-get install vim
sudo vim /etc/apt/sources.list
```

参考链接：  
[Ubuntu18.04下更改apt源为阿里云源](https://blog.csdn.net/zhangjiahao14/article/details/80554616)
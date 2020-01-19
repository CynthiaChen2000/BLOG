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
易看出sources.list文件中有格式：

> deb http://site.example.com/debian distribution component1 component2 component3  
> deb-src http://site.example.com/debian distribution component1 component2 component3

debian为自己Ubuntu版本的系统代号，后面几个参数是对软件包的分类（Ubuntu下是`main`， `restricted`，`universe`，`multiverse`这四个）。注释掉原来的源链接，改为任一国内镜像源：

阿里云源：
```
#  阿里源
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
```

中科大源：
```
#  中科大源
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
```

163源：
```
# 163源
deb http://mirrors.163.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-backports main restricted universe multiverse
```

清华源：
```
# 清华源
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe mul
```

4. 刷新列表
```
sudo apt-get update
sudo apt-get upgrade
```

参考链接：  
[Ubuntu 18.04下更改apt源为阿里云源](https://blog.csdn.net/zhangjiahao14/article/details/80554616)  
[Ubuntu 18.04 LTS 更换国内源——解决终端下载速度慢的问题](https://zhuanlan.zhihu.com/p/61228593)

## 三、Ubuntu安装软件  

deb格式：  
```
sudo dpkg -i ***.deb
```

参考链接：  
[Ubuntu下.deb安装包的四种安装方式](https://www.linmao.dev/joy/685/)
### 1. Goldendict

```
sudo apt-get install goldendict
sudo apt-get install goldendict goldendict-wordnet
```

如果要播放离线词库中的语音，需安装mplayer及其解码器：
```
sudo apt-get install mplayer
sudo apt-get install ubuntu-restricted-addons
sudo apt-get install ubuntu-restricted-extras
```
在线词典：

> 必应：https://cn.bing.com/dict/search?q=%GDWORD%  
> 有道：https://dict.youdao.com/search?q=%GDWORD%&ue=utf8  
> 百度：https://fanyi.baidu.com/#en/zh/%25GDWORD%25  
> 柯林斯：http://www.collinslanguage.com/results.aspx?context=3&reversed=False&action=define&homonym=-1&text=%GDWORD%  
> 金山词霸：http://www.iciba.com/%GDWORD%/  


参考链接：  
[ubuntu下安装goldendict及离线词库](https://blog.csdn.net/halazi100/article/details/44700631)

## 四、Linux同步远程仓库Github
```
sudo apt-get install git
git
ssh-keygen -t rsa
ls -a | grep .ssh
cd .ssh
ls
cat id_rsa.pub
```
检查是否配置成功：
```
ssh -T git@github.com
```
参考链接：  
[Linux本地仓库怎么向远程仓库（GitHub）提交代码](https://www.jianshu.com/p/1a35929311cb)

## 五、Linux快捷键
### 1. 截图
(1) Linux 中截图的默认方式
> PrtSc – 获取整个屏幕的截图并保存到 Pictures 目录  
> Shift + PrtSc – 获取屏幕的某个区域截图并保存到 Pictures 目录  
> Alt + PrtSc – 获取当前窗口的截图并保存到 Pictures 目录  
> Ctrl + PrtSc – 获取整个屏幕的截图并存放到剪贴板  
> Shift + Ctrl + PrtSc – 获取屏幕的某个区域截图并存放到剪贴板  
> Ctrl + Alt + PrtSc – 获取当前窗口的截图并存放到剪贴板  

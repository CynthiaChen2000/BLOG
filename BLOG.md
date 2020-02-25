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

### OBS Studio

####　一、环境

操作系统：Windows 10 64 位 中文家庭版
CPU 集成显卡型号：Intel® UHD Graphics 620
独立显卡型号：NVIDIA GeForce MX150
OBS Studio 版本：23.1.0 (64 bit)

#### 二、问题描述

我在 OBS Studio 的官网上下载安装了 OBS Studio, 但是，安装完成之后，在“来源”中添加“显示器捕获”之后预览框和录制得到的视频都是黑屏。

#### 三、解决过程

安装包是从官网下载的，安装过程没有报错，启动过程也没有报错，但是却捕捉不到显示器中的图像。首先考虑的是软件兼容性的问题，但是在我将兼容性设置成 "Windows 7"并且赋予 OBS Studio 管理员权限之后，录制得到的图像仍然是黑屏。这说明该问题的产生不是由于兼容性或者权限问题导致的，因此，随后我又将兼容性和权限恢复到了默认的状态。另一个需要考虑的问题就是显卡了。我的这台电脑有两个显卡，一个是英特尔 CPU 上的集成显卡，另一个是英伟达的独立显卡。根据我查找到的数据，OBS Studio 只能捕捉到和自己使用相同显卡的窗口或者程序。由于我是想要录制桌面的视频，因此，我在 Windows 10 的“任务管理器”中查看了“桌面窗口管理器(dwm.exe)”所使用的显卡是哪一个，结果发现，桌面窗口管理器使用的集成显卡。

根据上面的分析可以知道，只需要把 OBS Studio 使用的显卡设置成集成显卡应该就可以完成对屏幕的录制。首先打开“NVIDIA 设置”，依次打开“管理 3D 设置 / 程序设置”，之后使用“添加”按钮找到 OBS Studio 并添加，这时我发现，我这台电脑上的 OBS Studio 此时使用的是“高性能 NVIDIA 处理器”。

把 OBS Studio 使用的处理器更换成集成显卡。

之后重新打开 OBS Studio, 这时就可以录制桌面视频了。

参考链接：[解决OBS Studio录制的视频为黑屏的问题](https://blog.csdn.net/wy_bk/article/details/90439112)



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

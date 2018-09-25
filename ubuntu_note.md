# ubuntu笔记

## 修改源
### 1.为conda添加国内镜像
[Anaconda安装包](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)
安装后
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda congi --set show_channel_urls yes
```
之后，即可`conda install numpy`安装package.
### 2.为apt-get添加国内源
复制原文件备份 -> 编辑源列表文件 -> 将原来的列表删除，添加内容 -> 更新本地索引列表运行
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

sudo nano /etc/apt/sources.list

```
```
deb http://mirrors.aliyun.com/ubuntu/ vivid main restricted universe multiverse 
deb http://mirrors.aliyun.com/ubuntu/ vivid-security main restricted universe multiverse 
deb http://mirrors.aliyun.com/ubuntu/ vivid updates main restricted universe multiverse 
deb http://mirrors.aliyun.com/ubuntu/ vivid-proposed main restricted universe multiverse 
deb http://mirrors.aliyun.com/ubuntu/ vivid-backports main restricted universe multiverse 
deb-src http://mirrors.aliyun.com/ubuntu/ vivid main restricted universe multiverse 
deb-src http://mirrors.aliyun.com/ubuntu/ vivid-security main restricted universe multiverse 
deb-src http://mirrors.aliyun.com/ubuntu/ vivid-updates main restricted universe multiverse 
deb-src http://mirrors.aliyun.com/ubuntu/ vivid-proposed main restricted universe multiverse 
deb-src http://mirrors.aliyun.com/ubuntu/ vivid-backports main restricted universe multiverse

```
```
sudo apt-get update
sudo apt-get upgrade
```
### 3.为pip添加国内源
```bash
mkdir ~/.pip
nano ~/.pip/pip.conf
```
pip.conf文件编写如下内容：
```
[global] 
index-url = https://pypi.tuna.tsinghua.edu.cn/simple 
```
## 为ubuntu添加代理
首先将ss的允许其他设备连入打开，然后ipconfig找到本地ip地址作为`yourhost_ip`
1.export临时有效
```bash
export http_proxy=http://yourhost_ip:proxy_port
#取消使用
export http_proxy=""
```
2.apt.conf永久有效
```bash
sudo nano /etc/apt/apt.conf
```
加入以下内容
```
Acquire::http::Proxy "http://yourhost_ip:proxy_port";
```
3.bashrc文件中配置代理信息(apt-get,wget等等)全局有效
```bash
nano ~/.bashrc
```
添加以下内容
```bash
export http_proxy="http://yourhost_ip:proxy_port"
```
## 使用gui软件

```bash
sudo apt install dbus-x11
```
## 小知识点
1. ~：用户home目录
2. /：系统根目录


## 

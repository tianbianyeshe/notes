# ubuntu 知识点

1. ~：用户home目录
2. /：系统根目录
3. ifconfig ： ipconfighttps://www.jianshu.com/p/cd4d604e0b44)
4. [how to ssh into wsl or setup a ssh server](https://www.reddit.com/r/bashonubuntuonwindows/comments/5gh4c8/ssh_to_bash_on_wsl/)

  [or this](https://www.jianshu.com/p/cd4d604e0b44)
  
5. [how to reset wsl's username and password](https://docs.microsoft.com/en-us/windows/wsl/user-support)

6. apt-get 使用代理下载

export http_proxy=""命令并不能影响apt-get命令。有三种方式：
``` bash
#1 修改/etc/apt/apt.conf
Acquire::http::proxy "http://127.0.0.1:1080/";
Acquire::ftp::proxy "ftp://127.0.0.1:1080/";
Acquire::https::proxy "https://127.0.0.1:1080/";
#2 新建一个 ~/apt_proxy.conf 加入上面内容
sudo apt-get -c ~/apt_proxy.conf update/install
#3 
sudo apt-get -o Acquire::http::proxy="http://127.0.0.1:1080/" update/install 
```

7. start ssh 

``` bash
$ sudo /etc/init.d/ssh start

OR
$ sudo service ssh start

# OR for systemd based Ubuntu Linux 16.04 LTS or above server:
$ sudo systemctl start ssh 
```

8. copy file

```bash
$ cp [source] [target]


```
9. command list

|utility|command|
|-- | --|
|move file \a to \b and rename as c| mv /a /b/c|
|rename file| rename -v 's/strings/strings' *.nc|


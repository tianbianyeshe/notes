## ubuntu 设置全局代理

# shadowsocks
    sudo apt install python3-pip
    # to use method chacha20-ietf-poly1305
    pip3 install --upgrade git+https://github.com/shadowsocks/shadowsocks.git@master
/etc/shadowsock3.json

    {
       "server":"[server ip address]",
       "server_port":8388,
       "local_port":0,
       "password":"[password]",
       "timeout":600,
       "method":"aes-256-cfb"
    }
启动服务

    sudo sslocal -c /etc/shadowsocks.json -d start

# polipo

shadowsocks使用socks5协议通信，firefox和curl等应用使用http协议或https协议通信。
每次使用使用浏览器输入网址时，浏览器将数据组装成http格式的数据发送出去。
由于shadowsocks只能接受socks5格式的数据，因此在收到浏览器发送的http格式的数据时，提示unsupported socks protocol version 67等等错误信息。
firefox，curl等http应用需要polipo将http协议转换成socks5协议，才能使用shadowsocks代理上网。

    apt install polipo
    vim /etc/polipo/config
    
/etc/polipo/config

    # This file only needs to list configuration variables that deviate
    # from the default values.  See /usr/share/doc/polipo/examples/config.sample
    # and "polipo -v" for variables you can tweak and further information.
    logSyslog = true
    logFile = /var/log/polipo/polipo.log
    proxyAddress = "0.0.0.0"
    proxyPort = 17070
    socksParentProxy = "127.0.0.1:7070"
    socksProxyType = socks5
    allowedClients = 127.0.0.1
    
注意！复制的时候有可能前面自动加#，一定要在有用代码前删掉

    #重启服务
    service polipo stop
    service polipo start
    #设置http/https代理
    export http_proxy="http://127.0.0.1:17070" && export http_proxy="http://127.0.0.1:17070"
    #验证
    curl ip.gs
    curl 
    
## 开机自启动
[开机启动教程](kaiji.md)

在/etc/rc.local中的exit 0前添加

    sslocal -c /etc/shadowsocks.json -d start
    server polipo start
在~/.bashrc中添加

    export http_proxy="http://127.0.0.1:17070" && export http_proxy="http://127.0.0.1:17070"

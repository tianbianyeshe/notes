# 为docker设置代理
创建配置文件
    mkdir -p /etc/systemd/system/docker.service.d
    touch /etc/systemd/system/docker.service.d/http-proxy.conf
add these to the file
    
    [Service]
    Environment="HTTP_PROXY=http://proxy.example.com:80/"
注意！此处的地址应该是polipo的代理地址和端口

刷新systemd配置

    systemctl daemon-reload
用系统命令验证环境变量加上去没：

    $ systemctl show --property=Environment docker
    Environment=HTTP_PROXY=http://proxy.example.com:80/
重启docker
  $ sudo systemctl restart docker
  

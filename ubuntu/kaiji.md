# ubuntu 设置开机启动

1. create a service

    sudo vim /etc/systemd/system/rc-local.service
2. add these to file
    [Unit]
    Description=/etc/rc.local Compatibility
    ConditionPathExists=/etc/rc.local

    [Service]
    Type=forking
    ExecStart=/etc/rc.local start
    TimeoutSec=0
    StandardOutput=tty
    RemainAfterExit=yes
    SysVStartPriority=99

    [Install]
    WantedBy=multi-user.target

# ubuntu 设置开机启动

## 1. create a service

    sudo vim /etc/systemd/system/rc-local.service
## 2. add these to file

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
## 3. create and make /etc/rc/local executable
    #!/bin/sh -e
    #
    # rc.local
    #
    # This script is executed at the end of each multiuser runlevel.
    # Make sure that the script will "exit 0" on success or any other
    # value on error.
    #
    # In order to enable or disable this script just change the execution
    # bits.
    #
    # By default this script does nothing.

    exit 0
    
执行
    sudo chmod +x /etc/rc.local
## 4. Enable the service
    sudo systemctl enable rc-local
## 5. start service and check status
    sudo systemctl start rc-local.service
    sudo sytemctl status rc-local.service
## 6.add code to the /etc/rc.local file than restart service. 
remember code need to be before the exit 0

# Linux第一次实验作业

## Linux发行版本信息

### 查询代码

    rsb_release-a

### 代码内容

    No LSB modules are available.
    Distributor ID: Ubuntu
    Description:    Ubuntu 20.04.2 LTS
    Release:        20.04
    Codename:       focal

![avatar](/code_cmd.png)

## Linux内核版本信息

### 查询代码

    uname -a

### 代码内容

    UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

![avatar](code_uname.png)

***

## 关于网卡自启动和ip的自动获取

通过下列代码查询有：
    
    ip a
    cd /etc/netplan
    ls
    cat 00-installer-config.yaml

    network:
    ethernets:
    enp0s3:
      dhcp4: true
    enp0s8:
      dhcp4: true   /*网课自启动的原因*/
    version: 2

![avatar](查ip.png)
![avatar](网卡配置.png)

***

## 虚拟机与宿主机文件互传

    step 1：下载scp
![avatar](下载SCP.png)

    step 2: 虚拟机的端口转发设置
![avatar](端口转发.png)

    step 3： 进行WinSCP的操作设置
![avatar](WINSCP设置.png)

    step 3：登录后，界面实现
![avatar](最终界面.png)

## 本机和远程Linux系统之间文件互传

    1.新建一个测试文档于指定目录（/d:）
![avatar](测试文档.png)

    2.在服务器新建一个文件夹user用于测试
![avatar](新建文件夹.png)
    
    3.从本地上传到服务器
    scp -r /d:/test.txt cuc@192.168.56.101:user
![avatar](从本地上传到服务器.png)
![avatar](上传成功.png)

    4.从服务器加载文件到本地
    scp -r cuc@192.168.56.101:user/test1.txt /d:/
![avatar](新建服务器文件.png) 
![avatar](从服务器下载到本地.png)
![avatar](服务器到本地.png)
***

## ssh免密配置

### 代码

    ssh-keygen /* 配置公私钥对*/
    ssh-copy-id -i .ssh/id_rsa.pub cuc@192.168.56.101  /* 将秘钥写进远程操作端目录~/ .ssh/authorized_key.下*/
    ssh cuc@192.168.56.101 /*尝试免密登录*/

![avatar](配置公私钥对.png)
![avatar](发送文件到远程端.png)
![avatar](免密登录的实现.png)


<div>
  <img style="margin-top:-45px;width:1410px;height:225opx;" src="https://github.com/RyomaLiu/LetUsServer/blob/master/JustLet'sServer.assets/BookCover.PNG">
</div>





<div style="text-align:center;">
  <h1>
    前言
  </h1>
</div>

























<div style="text-align:center;">
  <h1>
    目录
  </h1>
</div>


[TOC]





------



# 1 虚拟机介绍

## 1.1 什么是虚拟机？

虚拟机是一种创建于物理硬件系统外部或者内部、充当虚拟计算机系统的虚拟环境，它模拟出了自己的整套硬件，包括CPU、内存、网络接口和存储器。通过虚拟机监控程序软件，用户可以将机器的资源与硬件分开并进行适当的配置以供虚拟机使用。

虚拟机允许在一台计算机上同时运行多个不同的操作系统，每个操作系统的运行方式与通常操作系统或者应用在主机硬件上使用的运行方式相同，因此在虚拟机中获得的最终用户体验与物理机上的实时操作系统体验几乎没有差别。配备了虚拟机监控程序的物理机被称为主机器，使用及资源的诸多虚拟机被称为虚拟客户机。

[^虚拟化]:虚拟化是虚拟机实现的重要概念。



## 1.2 为什么要使用虚拟机？

虚拟机可以提供一个与系统其余部分隔离开的环境。这样，无论虚拟机内部运行什么，都不会干扰主机硬件上运行的其他程序、服务。虚拟机隔离、独立于系统其它部分，而且单个硬件上可以有多个虚拟机，并可以根据自己的需要在主机服务器之间移动这些虚拟机，从而更有效地利用资源。

由于虚拟机处于隔离状态，因此是测试新应用以及设置生产环境的理想之选，此外，针对特定需求，还可以单独运行某一个虚拟机。

服务器整合也是使用虚拟机的重要原因。大多数操作系统和应用部署都只会使用少量的物力资源，如果直接部署到裸机时，会造成大量的物力资源被闲置。通过虚拟化服务器，可以在每个物理服务器上设置大量虚拟服务器，从而提高硬件利用率。

通过支持故障转移和冗余，虚拟机提供了额外的灾难恢复选项，以前这种功能只能通过增加硬件才能实现，有了虚拟机服务，便无需购买额外的物力资源，也不用过多考虑大量的物理硬件设备运行造成的放置空间和硬件运行冷却的需求。

## 1.3 虚拟机工作原理

虚拟化技术允许多个虚拟环境共享一个系统。虚拟机监控程序负责管理硬件并将物力资源与虚拟环境分隔开。虚拟机运行时，当用户或程序发出需要从物理环境获取更多资源指令，虚拟机监控程序会响应指令对物理环境资源进行调度，以便虚拟机的操作系统和应用可以访问共享物理资源池。

虚拟化有两种不同类型的虚拟机监控程序。

* **类型1**

  第一类虚拟机监控程序为裸机形式。

  虚拟机监控程序会直接向硬件调度虚拟机资源，KVM就是典型的第一类虚拟机监控程序。2007年开始，KVM已经被合并入Linux内核中。

* **类型2**

  第二类虚拟机监控程序为托管形式。

  虚拟机资源针对主机操作系统进行调度，然后针对硬件来执行。VMware Workstation和Oracle VirtualBox就是典型的第二类虚拟机监控程序。



# 2 虚拟机创建

## 2.1 安装VirtualBox

VirtualBox是一款开源虚拟机软件，本文也将使用VirtualBox创建虚拟机。

可以直接进入VirtualBox下载页面，根据电脑系统类型选择下载。

※ _URL：https://www.virtualbox.org/wiki/Downloads_

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906011539175.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      VirtualBox下载页面
    </figcaption>
  </center>
</figure>


笔者使用MacBookPro，这里下载了macOS系统对应的DMG安装文件（其他系统，下载系统相应的安装文件），编写本书时（2020年9月），VirtualBox最新版本是V6.1.14。

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="width:40%;border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906101701434.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      macOS-VirtualBox安装文件
    </figcaption>
  </center>
</figure>

双击打开DMG文件，按照提示双击`VirtualBox.pkg`文件即可开始安装（其他系统，按照平时软件安装流程进行安装）。

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906104649283.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      VirtualBox安装文件内容
    </figcaption>
  </center>
</figure>


介绍界面点击`继续`按钮，无需更改任何设置，使用默认设置点击`安装`按钮安装即可（系统可能要求输入用户密码认证）。

<figure style="display: flex;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906110946409.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      介绍
    </figcaption>
  </center>
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906111222459.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      安装类型
    </figcaption>
  </center>
</figure>
VirtualBox安装完成，在点击`关闭`按钮时会弹出询问是否要删除VirtualBox安装文件的对话框（因系统而异）：点击`保留`以保留安装文件，点击`移到废纸篓`以删除安装文件。

<figure style="display: flex;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906111446366.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      完成安装
    </figcaption>
  </center>
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906111509701.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      VirtualBox安装文件删除
    </figcaption>
  </center>
</figure>
启动VirtualBox后将呈现如同以下图片一样的界面，我们称之为VirtualBox管理器（在没有创建虚拟电脑的前提下，VirtualBox启动后进入的是欢迎页面）。

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906130543829.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      VirtualBox管理器
    </figcaption>
  </center>
</figure>
左侧面板为虚拟电脑列表，罗列所有已经创建的虚拟电脑。点击工具栏中菜单图标可以切换到

<figure style="display: flex;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200912234620096.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
    介质菜单
    </figcaption>
  </center>
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200912234811244.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
    介质管理
    </figcaption>
  </center>
</figure>

<figure style="display: flex;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200912234847664.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
    网络菜单
    </figcaption>
  </center>
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200912234903859.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
    网络管理
    </figcaption>
  </center>
</figure>






## 2.2 创建虚拟电脑

VirtualBox主界面点击`新建（N）`按钮，进入虚拟电脑名称和系统类型选择界面。

`名称`：输入要创建的虚拟电脑的名称（本文：CentOS8）

`文件夹`：选择虚拟电脑创建的目录

`类型`：选择将要创建虚拟电脑的类型（本文：Linux）

`版本`：会根据系统类型自动选择默认版本，如果默认选择不是目标版本，在版本列表中选择正确的目标版本

`内存大小`：默认为1024MB（1GB），可以根据自己当前电脑内存情况适当调整

`虚拟硬盘`：默认选择即可，可以根据个人安装需求调整

以上内容输入、调整完成之后，点击`创建`按钮进入虚拟硬盘文件类型选择界面。

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200902012433528.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      虚拟电脑名称、系统类型选择
    </figcaption>
  </center>
</figure>

虚拟硬盘文件类型选择界面中使用默认填充的信息即可。

`文件位置`：默认填充内容为上一界面中选择的虚拟电脑创建目录

`文件大小`：Linux系统类型默认为8GB

`虚拟硬盘文件类型`：默认选择VDI

`存储在物理硬盘上`：默认选择动态分配

按照自己需要调整配置内容之后，点击`创建`按钮完成虚拟电脑创建。

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200902012519686.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      虚拟硬盘文件类型、文件大小设置
    </figcaption>
  </center>
</figure>



<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200902012548028.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      虚拟电脑信息
    </figcaption>
  </center>
</figure>




## 2.2 添加虚拟光盘

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200913012907070.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
    右键菜单
    </figcaption>
  </center>
</figure>
选中新建的虚拟电脑，点击右侧面板上方工具栏中的`设置(S)`按钮，或者点击右键选择`设置...`选项，进入设置页面。

选择`存储`标签页，由于未添加虚拟光盘，此时控制器(IDE)显示为没有盘片。选择`没有盘片`，点击右侧属性面板`分配光驱`右侧的光盘图标，将会弹出可选`虚拟光驱`列表。

<figure style="display: flex;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200902012723809.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      存储标签页
    </figcaption>
  </center>
  <center style="padding: 10px;height:80%;">
    <img style="order:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200902012841325.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      虚拟光驱列表
    </figcaption>
  </center>
    <center style="padding: 10px;height:80%;">
    <img style="order:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200902012912754.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      虚拟光盘选择
    </figcaption>
  </center>
</figure>










<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200902012957341.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      虚拟电脑信息
    </figcaption>
  </center>
</figure>

## 2.3 CentOS系统安装

### 2.3.1 启动安装

![image-20200902013022154](./JustLet'sServer.assets/image-20200902013022154.png)





![image-20200902013104497](./JustLet'sServer.assets/image-20200902013104497.png)





![image-20200902013130972](./JustLet'sServer.assets/image-20200902013130972.png)





![image-20200902013203725](./JustLet'sServer.assets/image-20200902013203725.png)

### 2.3.2 设置安装

![image-20200902013353783](./JustLet'sServer.assets/image-20200902013353783.png)



![image-20200902013450866](./JustLet'sServer.assets/image-20200902013450866.png)



![image-20200902013739357](./JustLet'sServer.assets/image-20200902013739357.png)



![image-20200902013949871](./JustLet'sServer.assets/image-20200902013949871.png)



![image-20200902014022925](./JustLet'sServer.assets/image-20200902014022925.png)



![image-20200902014052714](./JustLet'sServer.assets/image-20200902014052714.png)



![image-20200902014117242](./JustLet'sServer.assets/image-20200902014117242.png)



![image-20200902014140534](./JustLet'sServer.assets/image-20200902014140534.png)



![image-20200902014245455](./JustLet'sServer.assets/image-20200902014245455.png)



![image-20200902014530102](./JustLet'sServer.assets/image-20200902014530102.png)



![image-20200902015414871](./JustLet'sServer.assets/image-20200902015414871.png)



![image-20200902015927459](./JustLet'sServer.assets/image-20200902015927459.png)



![image-20200902020530879](./JustLet'sServer.assets/image-20200902020530879.png)



![image-20200902020829411](./JustLet'sServer.assets/image-20200902020829411.png)





![image-20200902020900431](./JustLet'sServer.assets/image-20200902020900431.png)



![image-20200902020950410](./JustLet'sServer.assets/image-20200902020950410.png)



## 2.3 网络设置

### 2.3.1 测试网络

![image-20200902225211277](./JustLet'sServer.assets/image-20200902225211277.png)



### 2.3.2 设置网络

![image-20200902225400309](./JustLet'sServer.assets/image-20200902225400309.png)



![image-20200902225429251](./JustLet'sServer.assets/image-20200902225429251.png)



```shell
vi /etc/sysconfig/network-scripts/ifcfg-enp0s3
```



```shell
TYPE=Ethernet
PROXY_METHOD=none  
BROWSER_ONLY=no 
BOOTPROTO=dhcp → static
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=enp0s3
UUID=c1509e74-8d2b-4cab-bd17-60ab756c6b45
DEVICE=enp0s3
ONBOOT=no → yes
IPADDR=192.168.11.110 → 填写局域网内的IP地址
NETMASK=255.255.255.0
GATEWAY=192.168.11.1 → 填写局域网内网关地址
DNS1=8.8.8.8
DNS2=8.8.4.4
```



编辑完成后点击键盘[ESC]键退出编辑模式，键盘英文输入模式下输入[:wq]并点击回车保存修改。



```shell
nmcli c reload
nmcli c up enp0s3 # ifcfg-enp0s3:编辑文件名字中划线后部分
```



![image-20200902234020475](./JustLet'sServer.assets/image-20200902234020475.png)



## 2.4 SSH连接

### 2.4.1 终端工具

1. 终端（Terminal.app）
2. iTerm



### 2.4.2 连接

```shell
ssh root@192.168.11.110
```

连接问题

> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
>
> @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
>
> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
>
> IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
>
> Someone could be eavesdropping on you right now (man-in-the-middle attack)!
>
> It is also possible that a host key has just been changed.
>
> The fingerprint for the ECDSA key sent by the remote host is
>
> SHA256:2I1h6AFbCg+KWeF8FXlwNayUNnphl23BS7zxSZjQMMo.
>
> Please contact your system administrator.
>
> Add correct host key in /Users/Ryoma/.ssh/known_hosts to get rid of this message.
>
> Offending ECDSA key in /Users/Ryoma/.ssh/known_hosts:7
>
> ECDSA host key for 192.168.11.110 has changed and you have requested strict checking.
>
> Host key verification failed.

之前使用过相同的IP做过SSH连接，SSH Key在本地已经被存储，被存储的SSH Key和现在的服务器不匹配，导致SSH无法连接。



解决方法：

1. 手动删除SSH Key

   ```shell
   vi /Users/Ryoma/.ssh/known_hosts
   ```

   > 192.168.11.12 ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBMi/G+odq4E7arOfDY62gnw6j1qkervK9A32EzZxtTwouDXOeWRYh9Xk6fZc6pRDFC9DZQjbYiXte8lbXns8YwM=
   >
   > `192.168.11.110 ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBJZziVGHZj59FQWzrZ3ASKtGb647OU6HZzg0Uku8kFVbpTOSA4d1e8vfzvJo0hRVUgV2NDGfPE8XT3SEqb2XCsAo=` # 将旧的SSH Key删掉

   

2. 命令行删除SSH Key

   ```shell
   ssh-keygen -R 192.168.11.110
   ```

   命令会自动备份known_hosts为known_hosts.old



再次执行SSH连接命令

> RyomaLiu-MacBookPro:~ Ryoma$ ssh root@192.168.11.110
>
> The authenticity of host '192.168.11.110 (192.168.11.110)' can't be established.
>
> ECDSA key fingerprint is SHA256:2I1h6AFbCg+KWeF8FXlwNayUNnphl23BS7zxSZjQMMo.
>
> Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
>
> Warning: Permanently added '192.168.11.110' (ECDSA) to the list of known hosts.
>
> root@192.168.11.110's password:



## 2.5 YUM



### 2.5.1 什么是YUM？



### 2.5.2 YUM更新源切换

首先备份系统原有更新源文件

```shell
cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```



1. 清华大学开源软件镜像站

   > https://mirrors.tuna.tsinghua.edu.cn/help/centos/

   ![image-20200903004758024](./JustLet'sServer.assets/image-20200903004758024.png)





2. 阿里云

   > http://mirrors.aliyun.com/repo/

   ![image-20200903010345073](./JustLet'sServer.assets/image-20200903010345073.png)
   
   ```shell
   wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-8.repo
   ```
   
   如果执行时提示没有`wget`命令，可以使用YUM命令安装：
   
   ```shell
   yum -y install wget
   ```
   
   

### 2.5.3 YUM更新源更新

```shell
yum clean all
yum makecache
yum update
```

![image-20200903011135497](./JustLet'sServer.assets/image-20200903011135497.png)



![image-20200903013140988](./JustLet'sServer.assets/image-20200903013140988.png)





## 2.6 系统用户

### 2.6.1 创建系统用户



```shell
groupadd sysusr
useradd -g sysusr sysusr
```



查看是否添加成功

```shell
cat /etc/passwd
```



> root​​0:0:root:/root:/bin/bash
>
> bin​​1:1:bin:/bin:/sbin/nologin
>
> daemon​​2:2:daemon:/sbin:/sbin/nologin
>
> adm3:4:adm:/var/adm:/sbin/nologin
>
> lp4:7:lp:/var/spool/lpd:/sbin/nologin
>
> sync5:0:sync:/sbin:/bin/sync
>
> shutdown6:0:shutdown:/sbin:/sbin/shutdown
>
> halt​​7:0:halt:/sbin:/sbin/halt
>
> mail​​8:12:mail:/var/spool/mail:/sbin/nologin
>
> operator​​11:0:operator:/root:/sbin/nologin
>
> games​​12​​games:/usr/games:/sbin/nologin
>
> ftp​​14:50:FTP User:/var/ftp:/sbin/nologin
>
> nobody​​65534:65534:Kernel Overflow User:/:/sbin/nologin
>
> dbus​​81:81:System message bus:/:/sbin/nologin
>
> systemd-coredump​​999:997:systemd Core Dumper:/:/sbin/nologin
>
> systemd-resolve​​193:193:systemd Resolver:/:/sbin/nologin
>
> tss​​59:59:Account used by the trousers package to sandbox the tcsd daemon:/dev/null:/sbin/nologin
>
> polkitd​​998:996:User for polkitd:/:/sbin/nologin
>
> unbound​​997:994:Unbound DNS resolver:/etc/unbound:/sbin/nologin
>
> libstoragemgmt​​996:993:daemon account for libstoragemgmt:/var/run/lsm:/sbin/nologin
>
> setroubleshoot​​995:992::/var/lib/setroubleshoot:/sbin/nologin
>
> clevis​​994:990:Clevis Decryption Framework unprivileged user:/var/cache/clevis:/sbin/nologin
>
> cockpit-ws​​993:989:User for cockpit-ws:/nonexisting:/sbin/nologin
>
> sssd​​992:988:User for sssd:/:/sbin/nologin
>
> sshd​​74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
>
> chrony​​991:987::/var/lib/chrony:/sbin/nologin
>
> tcpdump​​72:72::/:/sbin/nologin
>
> mic.liu​​1000:1000:mic.liu:/home/mic.liu:/bin/bash
>
> cockpit-wsinstance​​990:986:User for cockpit-ws instances:/nonexisting:/sbin/nologin
>
> rngd​​989:985:Random Number Generator Daemon:/var/lib/rngd:/sbin/nologin
>
> `sysusr​​1001:1001::/home/sysusr:/bin/bash`



### 2.6.2 禁用系统用户登录



```shell
usermod -s /bin/false sysusr
```

为了验证是否禁用成功，首先设置一下系统用户登录密码

```shell
passwd sysusr
```

> RyomaLiu-MacBookPro:~ Ryoma$ ssh sysusr@192.168.11.110
>
> sysusr@192.168.11.110's password:
>
> Activate the web console with: systemctl enable --now cockpit.socket
>
> Last failed login: Wed Sep  2 12:55:00 EDT 2020 from 192.168.11.2 on ssh:notty
>
> There was 1 failed login attempt since the last successful login.
>
> Last login: Wed Sep  2 12:49:09 2020
>
> Connection to 192.168.11.110 closed.

可以看到登录失败，说明成功禁用系统用户登录。



同样也无法切换到系统用户

> [root@localhost ~]# su - sysusr
>
> [`sysusr`@localhost ~]$ exit  `→ 未禁用时可以切换到系统用户`
>
> logout
>
> [root@localhost ~]# usermod -s /bin/false sysusr `→ 禁用系统用户登录`
>
> [root@localhost ~]# `su - sysusr` `→ 尝试切换到系统用户`
>
> [`root`@localhost ~]# `→ 切换失败`



# 3 Nginx

## 3.1 什么是Nginx？





## 3.2 安装Nginx



### 3.2.1 Nginx检测

执行以下命令可以查看当前系统中是否已经安装Nginx，并可以查看安装的版本。

```shell
yum list installed nginx
```

如果当前系统中还未安装Nginx，执行以上查询命令后会输出类似下面的信息。

> [root@localhost ~]# yum list installed nginx
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Error: No matching Packages to list

如果当前系统已经安装Nginx，会出现以下信息。

> [root@localhost ~]# yum list installed nginx
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Installed Packages
>
> `nginx.x86_64         1:1.14.1-9.module_el8.0.0+184+e34fea82         @AppStream`



如果当前系统已经安装Nginx，但是版本并不是目标安装版本，可以执行以下命令移除已经安装的Nginx。

```shell
yum remove nginx
```



### 3.2.2 Nginx更新源

执行以下命令可以查看当前YUM更新源中是否有Nginx软件安装资源。如果YUM更新源中有Nginx软件安装资源，会列出可用Nginx版本信息。

```shell
yum list nginx
```

> [root@localhost ~]# yum list nginx
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Last metadata expiration check: 0:14:15 ago on Wed 02 Sep 2020 01:01:25 PM EDT.
>
> Available Packages
>
> `nginx.x86_64         1:1.14.1-9.module_el8.0.0+184+e34fea82         AppStream`

如果说当前YUM更新源中没有Nginx软件安装资源，可以手动添加Nginx软件安装资源到更新源中。

添加Nginx更新源文件：

```shell
vi /etc/yum.repos.d/nginx.repo
```

Nginx更新源文件内容：

> [nginx]
>
> name=nginx repo
>
> baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
>
> gpgcheck=0
>
> enabled=1



### 3.2.3 安装Nginx



```shell
yum -y install nginx
```



## 3.3 Nginx执行用户

将Nginx执行用户修改为系统用户。

```shell
vi /etc/nginx/nginx.conf
```

> \#For more information on configuration, see:
>
> \#   * Official English Documentation: http://nginx.org/en/docs/
>
> \#   * Official Russian Documentation: http://nginx.org/ru/docs/
>
> user `nginx`; → `sysusr` 
>
> worker_processes auto;
>
> error_log /var/log/nginx/error.log;
>
> pid /run/nginx.pid;
>
> \# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
>
> include /usr/share/nginx/modules/*.conf;

## 3.4 Nginx服务



### 3.4.1 Nginx服务启动/停止/重新启动/重新载入

* 启动

  ```shell
  systemctl start nginx.service 
  ```

  



* 停止

  ```shell
  systemctl stop nginx.service
  ```

  



* 重新启动

  ```shell
  systemctl restart nginx.service
  ```

  

* 重新载入

  ```shell
  systemctl reload nginx.service
  ```

  区别于上文的`重新启动`命令。



### 3.4.2 Nginx服务状态

使用下面命令可以查看当前Nginx服务状态：

```shell
systemctl status nginx.service
```

* 服务开启状态

  > [root@localhost ~]# systemctl status nginx.service
  >
  > ● nginx.service - The nginx HTTP and reverse proxy server
  >
  >    Loaded: loaded (/usr/lib/systemd/system/nginx.service; disabled; vendor preset: disabled)
  >
  >    Active: `active (running) since Thu 2020-09-03 10:52:56 EDT; 1s ago`
  >
  >   Process: 5318 ExecStart=/usr/sbin/nginx (code=exited, status=0/SUCCESS)
  >
  >   Process: 5316 ExecStartPre=/usr/sbin/nginx -t (code=exited, status=0/SUCCESS)
  >
  >   Process: 5315 ExecStartPre=/usr/bin/rm -f /run/nginx.pid (code=exited, status=0/SUCCESS)
  >
  >  Main PID: 5320 (nginx)
  >
  > ​    Tasks: 2 (limit: 5026)
  >
  >    Memory: 3.9M
  >
  >    CGroup: /system.slice/nginx.service
  >
  > ​           ├─5320 nginx: master process /usr/sbin/nginx
  >
  > ​           └─5321 nginx: worker process
  >
  > Sep 03 10:52:56 localhost.localdomain systemd[1]: Starting The nginx HTTP and reverse proxy server...
  >
  > Sep 03 10:52:56 localhost.localdomain nginx[5316]: nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
  >
  > Sep 03 10:52:56 localhost.localdomain nginx[5316]: nginx: configuration file /etc/nginx/nginx.conf test is successful
  >
  > Sep 03 10:52:56 localhost.localdomain systemd[1]: nginx.service: Failed to parse PID from file /run/nginx.pid: Invalid argument
  >
  > Sep 03 10:52:56 localhost.localdomain systemd[1]: Started The nginx HTTP and reverse proxy server.



* 服务停止状态

  > [root@localhost ~]# systemctl status nginx.service
  >
  > ● nginx.service - The nginx HTTP and reverse proxy server
  >
  >    Loaded: loaded (/usr/lib/systemd/system/nginx.service; disabled; vendor preset: disabled)
  >
  >    Active: `inactive (dead)`
  >
  > Sep 03 10:45:42 localhost.localdomain systemd[1]: Started The nginx HTTP and reverse proxy server.
  >
  > Sep 03 10:46:14 localhost.localdomain systemd[1]: Stopping The nginx HTTP and reverse proxy server...
  >
  > Sep 03 10:46:14 localhost.localdomain systemd[1]: Stopped The nginx HTTP and reverse proxy server.
  >
  > Sep 03 10:49:46 localhost.localdomain systemd[1]: Starting The nginx HTTP and reverse proxy server...
  >
  > Sep 03 10:49:46 localhost.localdomain nginx[5282]: nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
  >
  > Sep 03 10:49:46 localhost.localdomain nginx[5282]: nginx: configuration file /etc/nginx/nginx.conf test is successful
  >
  > Sep 03 10:49:46 localhost.localdomain systemd[1]: nginx.service: Failed to parse PID from file /run/nginx.pid: Invalid argument
  >
  > Sep 03 10:49:46 localhost.localdomain systemd[1]: Started The nginx HTTP and reverse proxy server.
  >
  > Sep 03 10:50:11 localhost.localdomain systemd[1]: Stopping The nginx HTTP and reverse proxy server...
  >
  > Sep 03 10:50:11 localhost.localdomain systemd[1]: Stopped The nginx HTTP and reverse proxy server.





### 3.4.3 Nginx欢迎页

类似于各种编程语言中编写`Hello world!`,如果没有修改过Nginx配置文件（nginx.conf）中的服务端口，Nginx默认为80端口。

在浏览器中输入` http://192.168.11.110（您的虚拟电脑IP）:80 `点击回车键，便可以看到Nginx欢迎页。

![image-20200904005044688](./JustLet'sServer.assets/image-20200904005044688.png)





不过您也有可能会看到以下画面：

![image-20200904003141296](./JustLet'sServer.assets/image-20200904003141296.png)



出现这个页面原因有两个：

1. Nginx服务未启动（启动失败或某种原因停止）
2. 系统开启了防火墙，Nginx服务端口未对外开放



### 3.4.5 开放Nginx服务端口

* 查看开放端口

  ```shell
  firewall-cmd --list-ports --zone=public
  ```

* 开放Nginx服务端口

  ```shell
  firewall-cmd --add-port=80/tcp --zone=public --permanent
  ```

  > [root@localhost ~]# firewall-cmd --add-port=80/tcp --zone=public --permanent
  >
  > success

  ```shell
  firewall-cmd --reload
  ```

  > [root@localhost ~]# firewall-cmd --reload
  >
  > success



* 关闭Nginx服务端口

  ```shell
  firewall-cmd --remove-port=80/tcp --zone=public --permanent
  ```

  > [root@localhost ~]# firewall-cmd --remove-port=80/tcp --zone=public --permanent
  >
  > success

  ```
  firewall-cmd --reload
  ```

  > [root@localhost ~]# firewall-cmd --reload
  >
  > success



* 可用服务列表

  ```shell
  firewall-cmd --get-services
  ```

  > [root@localhost ~]# firewall-cmd --get-services
  > RH-Satellite-6 amanda-client amanda-k5-client amqp amqps apcupsd audit bacula bacula-client bb bgp bitcoin bitcoin-rpc bitcoin-testnet bitcoin-testnet-rpc bittorrent-lsd ceph ceph-mon cfengine cockpit condor-collector ctdb dhcp dhcpv6 dhcpv6-client distcc dns dns-over-tls docker-registry docker-swarm dropbox-lansync elasticsearch etcd-client etcd-server finger freeipa-4 freeipa-ldap freeipa-ldaps freeipa-replication freeipa-trust ftp ganglia-client ganglia-master git grafana gre high-availability http https imap imaps ipp ipp-client ipsec irc ircs iscsi-target isns jenkins kadmin kdeconnect kerberos kibana klogin kpasswd kprop kshell kube-apiserver ldap ldaps libvirt libvirt-tls lightning-network llmnr managesieve matrix mdns memcache minidlna mongodb mosh mountd mqtt mqtt-tls ms-wbt mssql murmur mysql nfs nfs3 nmea-0183 nrpe ntp nut openvpn ovirt-imageio ovirt-storageconsole ovirt-vmconsole plex pmcd pmproxy pmwebapi pmwebapis pop3 pop3s postgresql privoxy prometheus proxy-dhcp ptp pulseaudio puppetmaster quassel radius rdp redis redis-sentinel rpc-bind rsh rsyncd rtsp salt-master samba samba-client samba-dc sane sip sips slp smtp smtp-submission smtps snmp snmptrap spideroak-lansync spotify-sync squid ssdp ssh steam-streaming svdrp svn syncthing syncthing-gui synergy syslog syslog-tls telnet tentacle tftp tftp-client tile38 tinc tor-socks transmission-client upnp-client vdsm vnc-server wbem-http wbem-https wsman wsmans xdmcp xmpp-bosh xmpp-client xmpp-local xmpp-server zabbix-agent zabbix-server

* 添加被允许服务

  ```shell
  firewall-cmd --add-service=http --zone=public --permanent
  firewall-cmd --reload
  ```

* 删除被允许服务

  ```shell
  firewall-cmd --remove-service=http --zone=public --permanent
  firewall-cmd --reload
  ```

* 查看以开放端口、服务

  ```shell
  firewall-cmd --list-all --zone=public
  firewall-cmd --list-services --zone=public
  firewall-cmd --list-ports --zone=public
  ```

  > [root@localhost ~]# firewall-cmd --list-all --zone=public
  >
  > public (active)
  >
  >   target: default
  >
  >   icmp-block-inversion: no
  >
  >   interfaces: enp0s3
  >
  >   sources:
  >
  >   services: cockpit dhcpv6-client ssh
  >
  >   ports: 80/tcp
  >
  >   protocols:
  >
  >   masquerade: no
  >
  >   forward-ports:
  >
  >   source-ports:
  >
  >   icmp-blocks:
  >
  >   rich rules:



### 3.4.4 Nginx自启动开启/关闭

1. 自动启动开启

   ```shell
   systemctl enable nginx.service    #Nginx自启动开启
   ```

   > [root@localhost ~]# systemctl enable nginx
   >
   > Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /usr/lib/systemd/system/nginx.service.

   ```shell
   systemctl daemon-reload    #重新载入配置文件
   ```

   

2. 自动开启关闭

   ```shell
   systemctl disable nginx.service
   ```

   > [root@localhost ~]# systemctl disable nginx
   >
   > Removed /etc/systemd/system/multi-user.target.wants/nginx.service.

   ```shell
   systemctl daemon-reload    #重新载入配置文件
   ```

   

# 4 PHP



## 4.1 PHP更新源添加

为了能够安装目标版本（8.0）的PHP，需要添加EPEL和Remi两个更新源。

* EPEL更新源

  ```shell
  rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
  ```

* Remi更新源

  ```shell
  rpm -Uvh http://rpms.remirepo.net/enterprise/remi-release-8.rpm
  ```

  ※ 当前虚拟电脑安装系统为CentOS8，所以以上的更新源响应的选择了`8`的版本，如需要可以选择其他版本。

<figure style="display: flex;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906214728620.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      EPEL更新源文件
    </figcaption>
  </center>
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200906214825122.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      Remi更新源文件
    </figcaption>
  </center>
</figure>



## 4.2 安装PHP



### 4.2.1 PHP检测

查看当前系统中是否已经安装PHP

```shell
yum list installed php*
```

> [root@localhost ~]# yum list installed php*
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Error: No matching Packages to list



> [root@localhost ~]# yum list installed php*
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Installed Packages
>
> php74.x86_64                   1.0-3.el8.remi      @remi-safe
>
> php74-php.x86_64               7.4.10-1.el8.remi   @remi-safe
>
> php74-php-cli.x86_64           7.4.10-1.el8.remi   @remi-safe
>
> php74-php-common.x86_64        7.4.10-1.el8.remi   @remi-safe
>
> php74-php-fpm.x86_64           7.4.10-1.el8.remi   @remi-safe
>
> php74-php-json.x86_64          7.4.10-1.el8.remi   @remi-safe
>
> php74-php-mbstring.x86_64      7.4.10-1.el8.remi   @remi-safe
>
> php74-php-opcache.x86_64       7.4.10-1.el8.remi   @remi-safe
>
> php74-php-pdo.x86_64           7.4.10-1.el8.remi   @remi-safe
>
> php74-php-sodium.x86_64        7.4.10-1.el8.remi   @remi-safe
>
> php74-php-xml.x86_64           7.4.10-1.el8.remi   @remi-safe
>
> php74-runtime.x86_64           1.0-3.el8.remi      @remi-safe





通过以上信息可以确定当前安装的Nginx的版本，如果当前安装的版本不是需要的版本，可以使用移除命令移除。

```shell
yum remove php*
```



### 4.2.2 PHP更新源



```
yum list php80*
```



> [root@localhost ~]# yum list php80*
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Last metadata expiration check: 0:17:11 ago on Sun 06 Sep 2020 08:49:30 AM EDT.
>
> Available Packages
>
> php80.x86_64             1.0-3.el8.remi            remi-safe
>
> php80-build.x86_64       1.0-3.el8.remi            remi-safe
>
> php80-php.x86_64         8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-ast.x86_64     1.0.9-1.el8.remi          remi-safe
>
> php80-php-bcmath.x86_64  8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-brotli.x86_64  0.11.1-2.el8.remi         remi-safe
>
> php80-php-cli.x86_64     8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-common.x86_64  8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-dba.x86_64     8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-dbg.x86_64     8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-devel.x86_64   8.0.0~beta3-31.el8.remi   remi-safe
>
> **`.......................此处省略.......................`**
>
> php80-php-snmp.x86_64    8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-soap.x86_64    8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-sodium.x86_64  8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-tidy.x86_64    8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-xml.x86_64     8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-xmlrpc.x86_64  8.0.0~DEV.20200526-13.el8.remi remi-safe
>
> php80-php-zstd.x86_64    0.9.0-3.el8.remi      remi-safe
>
> php80-php-zstd-devel.x86_64  0.9.0-3.el8.remi      remi-safe
>
> php80-runtime.x86_64     1.0-3.el8.remi            remi-safe
>
> php80-scldevel.x86_64    1.0-3.el8.remi            remi-safe
>
> php80-unit-php.x86_64    1.19.0-2.el8.remi         remi-safe
>
> 



### 4.2.3 安装PHP



```shell
yum -y install php80 php80-build php80-php
```











### 4.2.4 安装PHP扩展包



> [root@localhost ~]# yum list php80*
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Last metadata expiration check: 0:17:11 ago on Sun 06 Sep 2020 08:49:30 AM EDT.
>
> Available Packages
>
> php80.x86_64                1.0-3.el8.remi            remi-safe
>
> php80-build.x86_64          1.0-3.el8.remi            remi-safe
>
> **`.......................此处省略.......................`**
>
> `php80-php-ast`.x86_64        1.0.9-1.el8.remi          remi-safe
>
> php80-php-bcmath.x86_64     8.0.0~beta3-31.el8.remi   remi-safe
>
> php80-php-brotli.x86_64     0.11.1-2.el8.remi         remi-safe
>
> `php80-php-cli`.x86_64        8.0.0~beta3-31.el8.remi   remi-safe
>
> **`.......................此处省略.......................`**

如上，使用`yum list php80*`查询php可用安装包，`.x86_64`之前部分为扩展包名称，使用与PHP安装相同的命令安装扩展包，如果一次性安装多个扩展包，扩展包名称之间使用半角空格分隔。

```shell
yum -y install php80-php-ast php80-php-cli
```



## 4.3 PHP执行用户



```shell
vi /etc/opt/remi/php80/php-fpm.d/www.conf
```

> ; Start a new pool named 'www'.
>
> ; the variable $pool can be used in any directive and will be replaced by the
>
> ; pool name ('www' here)
>
> [www]
>
> **`.......................此处省略.......................`**
>
> ; Unix user/group of processes
>
> ; Note: The user is mandatory. If the group is not set, the default user's group
>
> ;       will be used.
>
> ; RPM: apache user chosen to provide access to the same directories as httpd
>
> user = `apache` → `sysusr`
>
> ; RPM: Keep a group allowed to write in log dir.
>
> group = `apache` → `sysusr`
>
> ; The address on which to accept FastCGI requests.
>
> ; Valid syntaxes are:
>
> ;   'ip.add.re.ss:port'    - to listen on a TCP socket to a specific IPv4 address on
>
> ;                            a specific port;
>
> ;   '[ip:6:addr:ess]:port' - to listen on a TCP socket to a specific IPv6 address on
>
> ;                            a specific port;
>
> ;   'port'                 - to listen on a TCP socket to all addresses
>
> ;                            (IPv6 and IPv4-mapped) on a specific port;
>
> ;   '/path/to/unix/socket' - to listen on a unix socket.
>
> ; Note: This value is mandatory.
>
> listen = /var/opt/remi/php80/run/php-fpm/www.sock
>
> ; Set listen(2) backlog.
>
> ; Default Value: 511
>
> ;listen.backlog = 511
>
> ; Set permissions for unix socket, if one is used. In Linux, read/write
>
> ; permissions must be set in order to allow connections from a web server.
>
> ; Default Values: user and group are set as the running user
>
> ;                 mode is set to 0660
>
> ;listen.owner = nobody
>
> listen.owner = `nobody` → `sysusr`
>
> ;listen.group = nobody
>
> listen.group = `nobody` → `sysusr`
>
> ;listen.mode = 0660
>
> listen.mode = 0660
>
> ; When POSIX Access Control Lists are supported you can set them using
>
> ; these options, value is a comma separated list of user/group names.
>
> ; When set, listen.owner and listen.group are ignored
>
> listen.acl_users = `apache` → `sysusr`
>
> ;listen.acl_groups =
>
> listen.acl_groups = `sysusr`
>
> ; List of addresses (IPv4/IPv6) of FastCGI clients which are allowed to connect.
>
> **`.......................此处省略.......................`**
>
> 



## 4.4 PHP服务



### 4.4.1 PHP服务启动/停止/重新启动/重新载入

* 启动

  ```shell
  systemctl start php80-php-fpm.service
  ```



* 停止

  ```shell
  systemctl stop php80-php-fpm.service
  ```



* 重新启动

  ```shell
  systemctl restart php80-php-fpm.service
  ```





* 重新载入

  ```shell
  systemctl reload php80-php-fpm.service
  ```

  





### 4.4.2 PHP服务状态



```shell
systemctl status php80-php-fpm.service
```

* 服务开启状态

  > [root@localhost ~]# systemctl status php80-php-fpm.service
  >
  > ● php80-php-fpm.service - The PHP FastCGI Process Manager
  >
  >    Loaded: loaded (/usr/lib/systemd/system/php80-php-fpm.service; disabled; vendor preset: disabled)
  >
  >    Active: `active (running) since Sun 2020-09-06 14:34:58 EDT; 1min 57s ago`
  >
  >  Main PID: 4560 (php-fpm)
  >
  >    Status: "Processes active: 0, idle: 5, Requests: 0, slow: 0, Traffic: 0req/sec"
  >
  > ​    Tasks: 6 (limit: 5026)
  >
  >    Memory: 23.8M
  >
  >    CGroup: /system.slice/php80-php-fpm.service
  >
  > ​           ├─4560 php-fpm: master process (/etc/opt/remi/php80/php-fpm.conf)
  >
  > ​           ├─4561 php-fpm: pool www
  >
  > ​           ├─4562 php-fpm: pool www
  >
  > ​           ├─4563 php-fpm: pool www
  >
  > ​           ├─4564 php-fpm: pool www
  >
  > ​           └─4565 php-fpm: pool www
  >
  > 
  >
  > Sep 06 14:34:58 localhost.localdomain systemd[1]: Starting The PHP FastCGI Process Manager...
  >
  > Sep 06 14:34:58 localhost.localdomain php-fpm[4560]: [06-Sep-2020 14:34:58] WARNING: [pool www] ACL set,listen.owner = 'sysusr' is i>
  >
  > Sep 06 14:34:58 localhost.localdomain php-fpm[4560]: [06-Sep-2020 14:34:58] WARNING: [pool www] ACL set,listen.group = 'sysusr' is i>
  >
  > Sep 06 14:34:58 localhost.localdomain systemd[1]: Started The PHP FastCGI Process Manager.
  >
  > 

* 服务停止状态

  > [root@localhost ~]# systemctl status php80-php-fpm.service
  >
  > ● php80-php-fpm.service - The PHP FastCGI Process Manager
  >
  >    Loaded: loaded (/usr/lib/systemd/system/php80-php-fpm.service; disabled; vendor preset: disabled)
  >
  >    Active: `inactive (dead)`
  >
  > Sep 06 14:34:58 localhost.localdomain systemd[1]: Starting The PHP FastCGI Process Manager...
  >
  > Sep 06 14:34:58 localhost.localdomain php-fpm[4560]: [06-Sep-2020 14:34:58] WARNING: [pool www] ACL set, listen.owner = 'sysusr' is i>
  >
  > Sep 06 14:34:58 localhost.localdomain php-fpm[4560]: [06-Sep-2020 14:34:58] WARNING: [pool www] ACL set, listen.group = 'sysusr' is i>
  >
  > Sep 06 14:34:58 localhost.localdomain systemd[1]: Started The PHP FastCGI Process Manager.
  >
  > Sep 06 14:40:13 localhost.localdomain systemd[1]: Stopping The PHP FastCGI Process Manager...
  >
  > Sep 06 14:40:13 localhost.localdomain systemd[1]: Stopped The PHP FastCGI Process Manager.
  >
  > 



### 4.4.3 PHP信息页



```shell
vi /usr/share/nginx/html/phpinfo.php
```

```php
<?php
  echo phpinfo();
?>
```



在浏览器中访问`http://192.168.11.110/phpinfo.php`，便可以查看PHP信息页。

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200907041524488.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      PHP页面被下载
    </figcaption>
  </center>
</figure>



```shell
vi /etc/nginx/nginx.conf
```



```shell
# For more information on configuration, see:
#   * Official English Documentation: http://nginx.org/en/docs/
#   * Official Russian Documentation: http://nginx.org/ru/docs/

user sysusr;
worker_processes auto;
error_log /var/log/nginx/error.log;
pid /run/nginx.pid;

# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
include /usr/share/nginx/modules/*.conf;

events {
    worker_connections 1024;
}

http {
    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         on;
    keepalive_timeout   65;
    types_hash_max_size 2048;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    # Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.
    include /etc/nginx/conf.d/*.conf;

    server {
        listen       80 default_server;
        listen       [::]:80 default_server;
        server_name  _;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        #location / {
        #}
        location / {
            if (!-e $request_filename){
                rewrite ^/(.*)$ /index.php/$1 last;
            }
        }

        location ~ \.php {
            fastcgi_pass unix:/var/opt/remi/php80/run/php-fpm/www.sock;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            include fastcgi_params;
            #定义变量 $path_info ，用于存放pathinfo信息
            set $path_info "";
            #定义变量 $real_script_name，用于存放真实地址
            set $real_script_name $fastcgi_script_name;
            #如果地址与引号内的正则表达式匹配
            if ($fastcgi_script_name ~ "^(.+?\.php)(/.+)$") {
                #将文件地址赋值给变量 $real_script_name
                set $real_script_name $1;
                #将文件地址后的参数赋值给变量 $path_info
                set $path_info $2;
            }
            #配置fastcgi的一些参数
            fastcgi_param SCRIPT_NAME $real_script_name;
            fastcgi_param PATH_INFO $path_info;
        }

        error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
    }

# Settings for a TLS enabled server.
#
#    server {
#        listen       443 ssl http2 default_server;
#        listen       [::]:443 ssl http2 default_server;
#        server_name  _;
#        root         /usr/share/nginx/html;
#
#        ssl_certificate "/etc/pki/nginx/server.crt";
#        ssl_certificate_key "/etc/pki/nginx/private/server.key";
#        ssl_session_cache shared:SSL:1m;
#        ssl_session_timeout  10m;
#        ssl_ciphers PROFILE=SYSTEM;
#        ssl_prefer_server_ciphers on;
#
#        # Load configuration files for the default server block.
#        include /etc/nginx/default.d/*.conf;
#
#        location / {
#        }
#
#        error_page 404 /404.html;
#            location = /40x.html {
#        }
#
#        error_page 500 502 503 504 /50x.html;
#            location = /50x.html {
#        }
#    }

}
```



```shell
systemctl restart nginx.service
```



<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200907051736438.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      PHP信息页面
    </figcaption>
  </center>
</figure>




### 4.4.4 PHP自启动开启/关闭

1. 自动启动开启

   ```shell
   systemctl enable php80-php-fpm.service    #Nginx自启动开启
   ```

   > [root@localhost ~]# systemctl enable php80-php-fpm.service
   >
   > Created symlink /etc/systemd/system/multi-user.target.wants/php80-php-fpm.service → /usr/lib/systemd/system/php80-php-fpm.service.

   ```shell
   systemctl daemon-reload    #重新载入配置文件
   ```

   

2. 自动开启关闭

   ```shell
   systemctl disable php80-php-fpm.service
   ```

   > [root@localhost ~]# systemctl disable php80-php-fpm.service
   >
   > Removed /etc/systemd/system/multi-user.target.wants/php80-php-fpm.service.

   ```shell
   systemctl daemon-reload    #重新载入配置文件
   ```

   







# 5 MySQL



## 5.1 MySQL更新源添加



```shell
rpm -Uvh http://dev.mysql.com/get/mysql80-community-release-el8-1.noarch.rpm
```



[MySQL Yum Repository](https://dev.mysql.com/downloads/repo/yum/)

<figure style="display: block;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200907070017357.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      MySQL Yum Repository
    </figcaption>
  </center>
</figure>



## 5.2 安装MySQL



### 5.2.1 MySQL检测



```shell
yum list installed mysql
```

> [root@localhost ~]# yum list installed mysql
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Error: No matching Packages to list







### 5.2.2 MySQL更新源



```shell
yum list mysql
```

> [root@localhost ~]# yum list mysql
>
> Repository AppStream is listed more than once in the configuration
>
> Repository extras is listed more than once in the configuration
>
> Repository PowerTools is listed more than once in the configuration
>
> Repository centosplus is listed more than once in the configuration
>
> Last metadata expiration check: 0:43:14 ago on Sun 06 Sep 2020 06:04:20 PM EDT.
>
> Available Packages
>
> mysql.x86_64  8.0.17-3.module_el8.0.0+181+899d6349   AppStream





### 5.2.3 安装MySQL



```shell
yum -y install mysql-server
```





## 5.3 MySQL服务

### 5.3.1 MySQL服务启动/停止/重新启动



* 启动

  ```shell
  systemctl start mysqld.service
  ```



* 停止

  ```shell
  systemctl stop mysqld.service
  ```



* 重新启动

  ```shell
  systemctl restart mysqld.service
  ```

  





### 5.3.2 MySQL服务状态



```shell
systemctl status mysqld.service
```

> [root@localhost ~]# systemctl status mysqld.service
>
> ● mysqld.service - MySQL 8.0 database server
>
>    Loaded: loaded (/usr/lib/systemd/system/mysqld.service; disabled; vendor preset: disabled)
>
>    Active: `active (running) since Sun 2020-09-06 19:25:24 EDT; 31min ago`
>
>   Process: 2877 ExecStopPost=/usr/libexec/mysql-wait-stop (code=exited, status=0/SUCCESS)
>
>   Process: 3010 ExecStartPost=/usr/libexec/mysql-check-upgrade (code=exited, status=0/SUCCESS)
>
>   Process: 2930 ExecStartPre=/usr/libexec/mysql-prepare-db-dir mysqld.service (code=exited, status=0/SUCCESS)
>
>   Process: 2905 ExecStartPre=/usr/libexec/mysql-check-socket (code=exited, status=0/SUCCESS)
>
>  Main PID: 2967 (mysqld)
>
>    Status: "Server is operational"
>
> ​    Tasks: 39 (limit: 5026)
>
>    Memory: 365.1M
>
>    CGroup: /system.slice/mysqld.service
>
> ​           └─2967 /usr/libexec/mysqld --basedir=/usr
>
> Sep 06 19:25:22 localhost.localdomain systemd[1]: Starting MySQL 8.0 database server...
>
> Sep 06 19:25:24 localhost.localdomain systemd[1]: Started MySQL 8.0 database server.



> [root@localhost ~]# systemctl status mysqld.service
>
> ● mysqld.service - MySQL 8.0 database server
>
>    Loaded: loaded (/usr/lib/systemd/system/mysqld.service; disabled; vendor preset: disabled)
>
>    Active: `inactive (dead)`
>
> Sep 06 19:24:41 localhost.localdomain systemd[1]: Starting MySQL 8.0 database server...
>
> Sep 06 19:24:41 localhost.localdomain mysql-prepare-db-dir[2694]: Initializing MySQL database
>
> Sep 06 19:24:52 localhost.localdomain systemd[1]: Started MySQL 8.0 database server.
>
> Sep 06 19:25:21 localhost.localdomain systemd[1]: Stopping MySQL 8.0 database server...
>
> Sep 06 19:25:22 localhost.localdomain systemd[1]: Stopped MySQL 8.0 database server.
>
> Sep 06 19:25:22 localhost.localdomain systemd[1]: Starting MySQL 8.0 database server...
>
> Sep 06 19:25:24 localhost.localdomain systemd[1]: Started MySQL 8.0 database server.
>
> Sep 06 23:43:15 localhost.localdomain systemd[1]: Stopping MySQL 8.0 database server...
>
> Sep 06 23:43:17 localhost.localdomain systemd[1]: Stopped MySQL 8.0 database server.



### 5.3.3 登录MySQL

* MySQL5.x登录密码

  对于MySQL5.x版本的安装，在完成安装时MySQL5.x版本会自动生成一个临时密码，并写入日志文件（/var/log/mysqld.log）。执行以下查询命令可以查看临时密码。

  ```shell
  grep 'temporary password' /var/log/mysqld.log
  ```

* MySQL8.x登录密码

  如果你尝试按照以往MySQL5.x的密码查询方法，你可能会失望了。

  > [root@localhost ~]# grep 'temporary password' /var/log/mysqld.log
  >
  > grep: /var/log/mysqld.log: No such file or directory

  可以看到在MySQL8.x版本中日志文件都未能找到，更确切地说是MySQL8.x的日志文件位置与MySQL5.x的日志文件不相同，MySQL8.x的日志文件位置为`/var/log/mysql/mysqld.log`。

  不过通过查看日志文件内容，可以看到MySQL8.x中并未设定临时密码。

  > [root@localhost ~]# cat /var/log/mysql/mysqld.log
  >
  > 2020-09-06T23:24:41.741610Z 0 [System] [MY-013169] [Server] /usr/libexec/mysqld (mysqld 8.0.17) initializing of server in progress as process 2731
  >
  > 2020-09-06T23:24:46.457613Z 5 [Warning] [MY-010453] [Server] `root@localhost is created with an empty password !` Please consider switching off the --initialize-insecure option.
  >
  > 2020-09-06T23:24:48.877151Z 0 [System] [MY-013170] [Server] /usr/libexec/mysqld (mysqld 8.0.17) initializing of server has completed
  >
  > 2020-09-06T23:24:50.906378Z 0 [System] [MY-010116] [Server] /usr/libexec/mysqld (mysqld 8.0.17) starting as process 2780
  >
  > 2020-09-06T23:24:52.393420Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
  >
  > 2020-09-06T23:24:52.438917Z 0 [System] [MY-010931] [Server] /usr/libexec/mysqld: ready for connections. Version: '8.0.17'  socket: '/var/lib/mysql/mysql.sock'  port: 3306  Source distribution.
  >
  > 2020-09-06T23:24:52.552126Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Socket: '/var/lib/mysql/mysqlx.sock' bind-address: '::' port: 33060
  >
  > 2020-09-06T23:25:22.492446Z 0 [System] [MY-010910] [Server] /usr/libexec/mysqld: Shutdown complete (mysqld 8.0.17)  Source distribution.
  >
  > 2020-09-06T23:25:23.114303Z 0 [System] [MY-010116] [Server] /usr/libexec/mysqld (mysqld 8.0.17) starting as process 2967
  >
  > 2020-09-06T23:25:24.439689Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
  >
  > 2020-09-06T23:25:24.473804Z 0 [System] [MY-010931] [Server] /usr/libexec/mysqld: ready for connections. Version: '8.0.17'  socket: '/var/lib/mysql/mysql.sock'  port: 3306  Source distribution.
  >
  > 2020-09-06T23:25:24.682727Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Socket: '/var/lib/mysql/mysqlx.sock' bind-address: '::' port: 33060
  >
  > 2020-09-07T03:43:17.557727Z 0 [System] [MY-010910] [Server] /usr/libexec/mysqld: Shutdown complete (mysqld 8.0.17)  Source distribution.



以下命令登录MySQL：

```shell
mysql -uroot
```

> [root@localhost ~]# mysql -uroot
>
> Welcome to the MySQL monitor.  Commands end with ; or \g.
>
> Your MySQL connection id is 8
>
> Server version: 8.0.17 Source distribution
>
> Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.
>
> Oracle is a registered trademark of Oracle Corporation and/or its
>
> affiliates. Other names may be trademarks of their respective
>
> owners.
>
> Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
>
> mysql>



### 5.3.4 root密码修改



```shell
alter user 'root'@'localhost' identified by '密码';
```



```shell
mysql -uroot -p
```

> [root@localhost ~]# mysql -uroot -p
>
> Enter password:
>
> Welcome to the MySQL monitor.  Commands end with ; or \g.
>
> Your MySQL connection id is 11
>
> Server version: 8.0.17 Source distribution
>
> Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.
>
> Oracle is a registered trademark of Oracle Corporation and/or its
>
> affiliates. Other names may be trademarks of their respective
>
> owners.
>
> Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
>
> mysql>



### 5.3.5 MySQL默认编码修改

修改MySQL配置文件。

```shell
vi /etc/my.cnf.d/mysql-server.cnf
```

> [mysqld]
>
> datadir=/var/lib/mysql
>
> socket=/var/lib/mysql/mysql.sock
>
> log-error=/var/log/mysql/mysqld.log
>
> pid-file=/run/mysqld/mysqld.pid
>
> `character_set_server=utf8`
>
> `init_connect='SET NAMES utf8'`

重新启动MySQL服务，是修改生效。

```shell
systemctl restart mysqld.service
```



### 5.3.6 MySQL自启动开启/关闭

1. 自动启动开启

   ```shell
   systemctl enable mysqld.service
   ```

   > [root@localhost ~]# systemctl enable mysqld.service
   >
   > Created symlink /etc/systemd/system/multi-user.target.wants/mysqld.service → /usr/lib/systemd/system/mysqld.service.

   ```shell
   systemctl daemon-reload
   ```

   

2. 自动开启关闭

   ```shell
   systemctl disable mysqld.service
   ```

   > [root@localhost ~]# systemctl disable mysqld.service
   >
   > Removed /etc/systemd/system/multi-user.target.wants/mysqld.service.

   ```shell
   systemctl daemon-reload
   ```

   

## 5.4 MySQL远程连接



### 5.4.1 添加MySQL远程用户

添加MySQL远程连接用户并赋予权限。

```shell
create user '用户名'@'%' identified by '密码';
grant all privileges on *.* to '用户名'@'%' with grant option;
flush privileges;
```

查看当前所有MySQL用户。

```shell
select host,user from mysql.user;
```

> mysql> select host,user from mysql.user;
>
> +-----------+------------------+
>
> \| host      \| user             \|
>
> +-----------+------------------+
>
> \| `%`         \| `remote_usr`       \|
>
> \| localhost \| mysql.infoschema \|
>
> \| localhost \| mysql.session    \|
>
> \| localhost \| mysql.sys        \|
>
> \| localhost \| root             \|
>
> +-----------+------------------+
>
> 5 rows in set (0.00 sec)

可以看到MySQL远程用户`remote_usr`已经添加成功。



### 5.4.2 远程连接MySQL

1. **查看MySQL服务端口**

   MySQL默认服务端口是`3306`，查看当前MySQL服务端口可以通过登录MySQL使用查询命令查看。

   ```shell
   show global variables like 'port';
   ```

   > mysql> show global variables like 'port';
   >
   > +---------------+-------+
   >
   > \| Variable_name \| Value \|
   >
   > +---------------+-------+
   >
   > \| port          \| `3306` \|
   >
   > +---------------+-------+
   >
   > 1 row in set (0.02 sec)

   可以看到当前MySQL使用的为默认端口。

   

2. **修改MySQL服务端口**

   ```shell
   vi /etc/my.cnf.d/mysql-server.cnf
   ```

   > [mysqld]
   >
   > datadir=/var/lib/mysql
   >
   > socket=/var/lib/mysql/mysql.sock
   >
   > log-error=/var/log/mysql/mysqld.log
   >
   > pid-file=/run/mysqld/mysqld.pid
   >
   > character_set_server=utf8
   >
   > init_connect='SET NAMES utf8'
   >
   > `port=33066`

   修改完MySQL配置，重启MySQL服务。

   ```shell
   systemctl restart mysqld.service
   ```

   登录MySQL查看端口是否更改。

   > mysql> show global variables like 'port';
   >
   > +---------------+-------+
   >
   > \| Variable_name \| Value \|
   >
   > +---------------+-------+
   >
   > \| port          \| `33066` \|
   >
   > +---------------+-------+
   >
   > 1 row in set (0.02 sec)

   

3. **远程连接MySQL**

   开放MySQL现在使用的端口

   ```shell
   firewall-cmd --add-port=33066/tcp --zone=public --permanent
   firewall-cmd --reload
   ```

   主机系统端利用数据库访问软件（MySQLWorkbench或者其他可用软件）远程连接MySQL。

   <figure style="display: flex;">
     <center style="padding: 10px;width:50%;height:100%;">
       <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200907204613188.png">
       <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
         MySQLWorkbench连接
       </figcaption>
     </center>
     <center style="padding: 10px;width:50%;height:100%;">
       <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200907204657171.png">
       <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
         测试连接成功
       </figcaption>
     </center>
   </figure>





# 6 安装openJDK





```shell
dnf -y install java-11-openjdk java-11-openjdk-devel
```

<figure style="display: flex;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200908014416909.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      openjdk安装
    </figcaption>
  </center>
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200908014628219.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      openjdk安装
    </figcaption>
  </center>
</figure>

查看jdk命令

```shell
java -version
```

> [root@localhost ~]# java -version
>
> openjdk version "11.0.8" 2020-07-14 LTS
>
> OpenJDK Runtime Environment 18.9 (build 11.0.8+10-LTS)
>
> OpenJDK 64-Bit Server VM 18.9 (build 11.0.8+10-LTS, mixed mode, sharing)





```shell
dnf -y install java-1.8.0-openjdk java-1.8.0-openjdk-devel
```





<figure style="display: flex;">
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200908021233779.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      openjdk安装
    </figcaption>
  </center>
  <center style="padding: 10px;">
    <img style="border:0.2px solid #eee;border-radius:5px;" src="./JustLet'sServer.assets/image-20200908021412873.png">
    <figcaption style="border-bottom: 1px solid #eee;width:fit-content;padding:5px 5px 1px;">
      openjdk安装
    </figcaption>
  </center>
</figure>

现在系统选中安装了jdk11和jdk1.8，可以使用命令随时选择使用哪一个。

```shell
alternatives --config java
```

> [root@localhost ~]# alternatives --config java
>
> There are 2 programs which provide 'java'.
>
>   Selection    Command
>
> \-----------------------------------------------
>
>  \+ 1           java-11-openjdk.x86_64 (/usr/lib/jvm/java-11-openjdk-11.0.8.10-0.el8_2.x86_64/bin/java)
>
> \*  2           java-1.8.0-openjdk.x86_64 (/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.262.b10-0.el8_2.x86_64/jre/bin/java)
>
> Enter to keep the current selection[+], or type selection number: `2`

```shell
alternatives --config javac
```

> [root@localhost ~]# alternatives --config javac
>
> There are 2 programs which provide 'javac'.
>
>   Selection    Command
>
> \-----------------------------------------------
>
>  \+ 1           java-11-openjdk.x86_64 (/usr/lib/jvm/java-11-openjdk-11.0.8.10-0.el8_2.x86_64/bin/javac)
>
> \*  2           java-1.8.0-openjdk.x86_64 (/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.262.b10-0.el8_2.x86_64/bin/javac)
>
> Enter to keep the current selection[+], or type selection number:`2`

在是jdk1.8有效之前可以看到当前是jdk11有效，在选项中输入2选择使用jdk1.8。

此时再用Java版本查看命令查看当前Java版本

> [root@localhost ~]# java -version
>
> openjdk version "`1.8.0_262`"
>
> OpenJDK Runtime Environment (build 1.8.0_262-b10)
>
> OpenJDK 64-Bit Server VM (build 25.262-b10, mixed mode)



```shell
vi JavaTest.java
```



```java
class JavaTest {
    public static void main(String[] args){
        System.out.println("Let's Server!");
    }
}
```



```shell
javac JavaTest.java
java JavaTest
```





```shell
vi .bash_profile
```

> export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.262.b10-0.el8_2.x86_64/jre/bin/java

刷新`.bash_profile`

```shell
source .bash_profile
```

查看JAVA_HOME添加是否生效

```shell
echo $JAVA_HOME
```

> [root@localhost ~]# echo $JAVA_HOME
>
> /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.262.b10-0.el8_2.x86_64/jre/bin/java







# 7 GlassFish



## 7.1 



```shell
wget https://download.oracle.com/glassfish/4.1.2/release/glassfish-4.1.2.zip
```



```shell
unzip -d /opt/ glassfish-4.1.2.zip
```

解压完毕后



```shell
chown -R sysusr:sysusr /opt/glassfish4/
```



创建GlassFish服务

```shell
vi /usr/lib/systemd/system/glassfish.service
```

> [Unit]
>
> Description = GlassFish Server v4.1.2
>
> After = syslog.target network.target
>
> [Service]
>
> User = sysusr
>
> ExecStart = /usr/bin/java -jar /opt/glassfish4/glassfish/lib/client/appserver-cli.jar start-domain
>
> ExecStop = /usr/bin/java -jar /opt/glassfish4/glassfish/lib/client/appserver-cli.jar stop-domain
>
> ExecReload = /usr/bin/java -jar /opt/glassfish4/glassfish/lib/client/appserver-cli.jar restart-domain
>
> Type = forking
>
> [Install]
>
> WantedBy = multi-user.target



```shell
systemctl start glassfish.service
```



```shell
systemctl enable glassfish.service
```

> [root@localhost ~]# systemctl enable glassfish.service
>
> Created symlink /etc/systemd/system/multi-user.target.wants/glassfish.service → /usr/lib/systemd/system/glassfish.service.

```shell
systemctl daemon-reload
```





开放端口

```shell
firewall-cmd --add-port={4848,8080,8181}/tcp --permanent
```

> [root@localhost ~]# firewall-cmd --add-port={4848,8080,8181}/tcp --permanent
>
> success

```shell
firewall-cmd --reload
```

> [root@localhost ~]# firewall-cmd --reload
>
> success



PATH中添加GlassFish目录

```shell
vi .bash_profile
```

> PATH=$PATH:/opt/glassfish5/bin/

```shell
source .bash_profile
```



```shell
asadmin --port 4848 change-admin-password
```

> [root@localhost ~]# asadmin --port 4848 change-admin-password
>
> Enter admin user name [default: admin]>admin
>
> Enter the admin password>`默认密码为空，此处直接按下回车键`
>
> Enter the new admin password>
>
> Enter the new admin password again>
>
> Command change-admin-password executed successfully.



允许远程连接

```shell
asadmin --port 4848 enable-secure-admin
```

> [root@localhost ~]# asadmin --port 4848 enable-secure-admin
>
> Enter admin user name>  admin
>
> Enter admin password for user "admin">
>
> You must restart all running servers for the change in secure admin to take effect.
>
> Command enable-secure-admin executed successfully.



重启GlassFish服务

```shell
systemctl restart glassfish.service
```











































# 可能遇到的问题

## 1 Nginx测试页请求应答403页面

### 1 请求应答403页面

以下的两种情况下可能会出现拒绝访问页面：
* 完成Nginx安装，尝试访问Nginx欢迎页面（测试页）时。
* 添加新的Nginx工作目录之后，尝试访问页面。

<figure style="display: flex;">
  <center style="padding: 2px;">
    <img src="/Users/Ryoma/RyomaWork/00_Work/03_MarkDown/LINUX服务器搭建.assets/image-20200830230429534.png">
    <div style="border-bottom: 1px solid #cccccc;width:fit-content;padding:5px;">
      403 Forbidden
    </div>
  </center>
</figure>
### 2 原因及解决方案

#### 2.1 Nginx服务器未重启

* 原因

  如果修改了Nginx配置文件，未重启Nginx服务，则修改将无法被适用。首先确认在修改过Nginx配置文件之后，是否重启了Nginx服务。

* 解决方案

  重启Nginx服务，再次尝试访问。

  ```shell
  systemctl restart nginx.service #首先停止Nginx服务在启动Nginx服务
  ```

  ```shell
  systemctl reload nginx.service #不会停止Nginx服务，仅适用修改配置
  ```

#### 2.2 URL访问被限制

* 原因

  访问的URL可能属于Nginx被限制访问的特定URL，查看Nginx配置文件，确定访问的URL是否是被限制的URL。

  ```shell
  cat /etc/nginx/conf.d/webproj0000.conf #自己访问应用所在的服务器
  ```

  >...
  >
  >location / {
  >
  >​    root   /var/app/webproj/WebProj0000;
  >
  >​    index  index.html index.htm;
  >
  >​    `deny all;`    # 所有的请求将被拒绝 
  >
  >} 
  >... 

  如果Nginx配置文件中有上面` deny all; `的设置，说明URL访问被限制。

* 解决方案

  1. 允许所有访问

     如果没有特殊需求，可以将Nginx访问设定修改为允许所有访问。

     > ...
     >
     > location / {
     >
     > ​    root   /var/app/webproj/WebProj0000;
     >
     > ​    index  index.html index.htm; 
     >
     > ​    `allow all;`    # 允许所有访问 
     >
     > } 
     > ... 

  2. 允许特定IP访问

     Nginx访问设定同时也支持只允许特定的IP访问。

     > ...
     >
     > location / {
     >
     > ​    root   /var/app/webproj/WebProj0000; 
     >
     > ​    index  index.html index.htm; 
     >
     > ​    `allow 192.168.11.4;` # 允许特定IP访问 
     >
     > ​    deny all;  
     >
     > } 
     > ... 

#### 2.3 文件无读取权限

* 原因

  系统其它用户对于访问文件没有读取权限，导致被拒绝访问。

  查看系统其他用户权限：

  ```shell
  ls -l /var/app/webproj/WebProj0000/index.html
  ```

  > -rw-r--`---`. 1 root root 465 Aug 30 01:20 /var/app/webproj/WebProj0000/index.html

  命令行输出中看到`---`，说明系统其它用户没有任何权限。

* 解决方案

  为系统其它用户添加文件读取权限：

  ```shell
  sudo chmod o+r /var/app/webproj/WebProj0000/index.html
  ```

  > -rw-r--`r--`. 1 root root 465 Aug 30 01:20 /var/app/webproj/WebProj0000/index.html

#### 2.4 工作目录无执行权限

* 原因

  DocumentRoot的各层级目录中，系统其它用户如果对于其中任何一个目录没有执行权限，会出现拒绝访问。

  ```shell
  ls -ld /var/app/webproj/WebProj0000
  ```

  > drwxr-x`r--`. 5 root root 56 Aug 30 18:51 /var/app/webproj/WebProj0000

  如果命令行输出系统其它用户权限是`r--`，说明系统其它用户对于这个目录没有执行权限。

* 解决方案

  为系统其它用户添加目标目录的执行权限。

  ```shell
  sudo chmod o+x /var/app/webproj/WebProj0000
  ```

  再次查看系统其它用户的目标目录权限。

  ```shell
  ls -ld /var/app/webproj/WebProj0000
  ```

  > drwxr-x`r-x`. 5 root root 56 Aug 30 18:51 /var/app/webproj/WebProj0000

#### 2.5 SELinux被启用

* 原因

  SELinux模块被启用，可能会导致DocumentRoot无法访问，首先确认一下当前系统中SELinux是否被启用。

  SELinux启用状态确认命令行： 

  ```shell
  getenforce
  ```

  如果命令行输出`Enforcing`，说明SELinux模块被启用，可以按照`👇`以下解决方案尝试解决问题。

  如果命令行输出`Disabled`，说明SELinux模块未被启用。

* 解决方案

  - SELinux无效化

    如果项目中没有必须开启SELinux的情况下，可以将SELinux无效化：

    ```shell
    sudo vi /etc/selinux/config #修改配置文件
    ```

    > \# This file controls the state of SELinux on the system.
    >
    > \# SELINUX= can take one of these three values:
    >
    > \#     enforcing - SELinux security policy is enforced.
    >
    > \#     permissive - SELinux prints warnings instead of enforcing.
    >
    > \#     disabled - No SELinux policy is loaded.
    >
    > SELINUX=`disabled`	←   将`enforcing`改为`disabled` 
    >
    > \# SELINUXTYPE= can take one of these three values:
    >
    > \#     targeted - Targeted processes are protected,
    >
    > \#     minimum - Modification of targeted policy. Only selected processes are protected.
    >
    > \#     mls - Multi Level Security protection.
    >
    > SELINUXTYPE=targeted

    修改完配置文件之后需要重启服务器：

    ```shell
    sudo shutdown -r now
    ```
    
    服务器重启之后执行SELinux启用状态确认命令，如果命令行输出Disabled说明SELinux模块已经无效化。
  
  
  
  - 修改目录安全上下文
  
    参照Nginx原始工作目录安全上下文，为新添加的工作目录添加相同的安全上下文。
  
    查看Nginx原始工作目录以及新添加工作目录安全上下文：
  
    ```shell
    ls -ld --context /usr/share/nginx/html
    ```
  
    > drwxr-xr-x. 2 root root system_u:object_r:httpd_sys_content_t:s0
    >
    > 114 Aug 27 12:45 /usr/share/nginx/html
  
    ```shell
    ls -ld --context /var/app/webproj/WebProj0000
    ```
  
    > drwxr-xr-x. 5 root root unconfined_u:object_r:var_t:s0 56 Aug 30 01:20 /var/app/webproj/WebProj0000
  
    更改新添加工作目录安全上下文：
  
    ```shell
    sudo chcon system_u:object_r:httpd_sys_content_t:s0 /var/app/webproj/WebProj0000 -R
    ```
  
    修改完新添加工作目录安全上下文后，确认是否修改成功：
  
    ```shell
    ls -ld --context /var/app/webproj/WebProj0000
    ```
  
    > drwxr-xr-x. 5 root root `system_u:object_r:httpd_sys_content_t:s0` 56 Aug 30 01:20 /var/app/webproj/WebProj0000





# LINUX豆知识

## 1 理解Linux文件/目录权限

### 1.1 查看权限

Linux查看文件/目录权限有多重形式，常用有以下两种：

1. 查看当前目录下所有文件/目录权限

   ```shell
   ls -l
   ```

   > `lrwxrwxrwx`.  1 root root       38 Aug 16 07:59 localtime -> ../usr/share/zoneinfo/America/New_York
   > `-rw-r--r--`.  1 root root     2027 Nov  8  2019 login.defs
   > -rw-r--r--.  1 root root      438 Feb 19  2018 logrotate.conf
   > `drwxr-xr-x`.  2 root root      232 Aug 26 13:40 logrotate.d
   > drwxr-xr-x.  3 root root       43 Apr 23 22:54 lsm
   > drwxr-xr-x.  6 root root      100 Aug 16 14:08 lvm
   > -r--r--r--.  1 root root       33 Aug 16 07:49 machine-id
   > -rw-r--r--.  1 root root      111 Apr  6 20:15 magic
   > -rw-r--r--.  1 root root      272 May 11  2017 mailcap
   > -rw-r--r--.  1 root root     5122 Apr 24 13:07 makedumpfile.conf.sample
   > -rw-r--r--.  1 root root     5165 May 11  2019 man_db.conf
   > drwxr-xr-x.  3 root root       41 Apr  6 23:07 mcelog
   > drwxr-xr-x.  3 root root       32 Jun 25 10:39 microcode_ctl

   命令行输出结果中









# YUM命令集锦









# PHP更新源--可用安装包

  ```php
php{Ver}-php-snuffleupagus:x86_64: PHP的安全模块
php{Ver}-php-pecl-cassandra:用于Apache的DataStax PHP驱动程序卡桑德拉
php{Ver}-php-pecl-nsq:NSQ客户端的PHP扩展
php{Ver}-php-cli:用于PHP的命令行接口
php{Ver}-php-pecl-oauth:PHP OAuth消费者扩展
php{Ver}-php-pecl-decimal:任意精度浮点小数
php{Ver}-php-gmp:一个用于使用GNU的PHP应用程序模块议员库
php{Ver}-php-pecl-rdkafka4:基于librdkafka的Kafka客户端
php{Ver}-php-soap:用于使用SOAP的PHP应用程序的模块协议
php{Ver}-php-phpiredis:x86_64: Redis的客户端扩展名
php{Ver}-php-pecl-taint:x86_64: XSS代码嗅探器
php{Ver}-php-pecl-redis4:的扩展名 Redis键值存储
php{Ver}-php-pecl-propro-devel:php{Ver}-php-pecl-propro developer files (header)
php{Ver}-php-pecl-psr-devel:php{Ver}-php-pecl-psr developer files (header)
php{Ver}-php-pecl-redis5:的扩展名 Redis键值存储
php{Ver}-zephir:用于创建扩展的Zephir语言PHP
php{Ver}-php-pecl-selinux:用于PHP脚本的SELinux绑定语言
php{Ver}-php-pecl-rdkafka:基于librdkafka的Kafka客户端
php{Ver}-php-pecl-grpc:x86_64:通用RPC框架
php{Ver}-php-brotli:用于PHP的Brotli扩展
php{Ver}-php-pecl-http-message-devel:php{Ver}-php-pecl-http-message developer files (headers)
php{Ver}-php-pecl-fann:用于FANN库的包装器
php{Ver}-php-pecl-yaz:x86_64: Z39.50/SRU客户端
php{Ver}-php-lz4:x86_64: PHP的LZ4扩展
php{Ver}-php-libvirt:用于Libvirt的PHP语言绑定
php{Ver}-php-pecl-zmq:ZeroMQ消息传递
php{Ver}-php-pecl-mongodb:x86_64:用于PHP的MongoDB驱动程序
php{Ver}-php-process:用于PHP脚本的模块使用系统进程接口
php{Ver}-php-zephir-parser-devel:php{Ver}-php-zephir-parser developer files (headers)
php{Ver}-php-pspell:x86_64:用于PHP应用程序的模块中接口
php{Ver}-php-pecl-yar:轻量级并发RPC框架
php{Ver}-php:用于创建动态web的PHP脚本语言网站
php{Ver}-php-pecl-rrd:x86_64: rrdtool的PHP绑定
php{Ver}-runtime:处理php{Ver}软件集合的包
php{Ver}-php-pecl-xmldiff-devel:php{Ver}-php-pecl-xmldiff developer files (header)
php{Ver}-php-pecl-hprose:用于PHP的h散文
php{Ver}-php-pecl-propro:属性代理
php{Ver}-php-pecl-yac:无锁用户数据缓存
php{Ver}-php-pecl-csv:CSV PHP extension
php{Ver}-php-pecl-swoole4:PHP的异步并发分布式网络框架
php{Ver}-php-pecl-pcov:x86_64:代码覆盖驱动程序
php{Ver}-php-pecl-sync:已命名和未命名同步对象
php{Ver}-php-pecl-yaf:x86_64:又一个框架
php{Ver}-php-pecl-varnish:Varnish缓存绑定
php{Ver}-php-pggi:GTK绑定
php{Ver}-php-pecl-handlebars:Handlebars模板语言
php{Ver}-php-pecl-rar:用于读取RAR存档的PHP扩展
php{Ver}-php-pecl-xdebug:用于调试PHP脚本的PECL包
php{Ver}-php-oci8:x86_64:用于使用OCI8的PHP应用程序的模块数据库
php{Ver}-php-fpm:PHP FastCGI进程管理器
php{Ver}-php-common:PHP的公共文件
php{Ver}-php-pecl-xlswriter:一个高效、快速的xlsx文件出口扩展
php{Ver}-php-pecl-stats:用于统计计算的例程
php{Ver}-php-pecl-krb5:Kerberos验证扩展
php{Ver}-php-pecl-xhprof:x86_64: XHProf的PHP扩展，层次结构分析器
php{Ver}-php-pecl-ssdeep:libfuzzy库的包装器
php{Ver}-php-pecl-imagick:x86_64:用于创建和修改映像的扩展使用ImageMagick
php{Ver}-php-pecl-apcu-bc:APCu向后兼容模块
php{Ver}-php-xml:x86_64:用于使用XML的PHP应用程序的模块
php{Ver}-php-sodium:x86_64:钠密码库的包装
php{Ver}-php-pecl-apfd:总是填充表单数据
php{Ver}-php-componere:在运行时编写PHP类
php{Ver}-php-pecl-cmark:CommonMark扩展名
php{Ver}-php-pecl-uploadprogress:x86_64:跟踪进度的扩展文件上传
php{Ver}-php-pecl-apcu-devel:APCu开发人员文件(头文件)
php{Ver}-php-devel:构建PHP扩展所需的文件
php{Ver}-php-pecl-http-message:x86_64: PSR-7 HTTP消息实现
php{Ver}-xhprof:一个用于PHP - Web接口的层次分析器
php{Ver}-php-pear:noarch: PHP扩展和应用程序库框架
php{Ver}-php-pecl-igbinary:x86_64:替代标准PHP序列化器
php{Ver}-php-pecl-sdl:简单的PHP DirectMedia层
php{Ver}-php-pecl-parle:x86_64:解析和词法分析
php{Ver}-php-pecl-zip:一个ZIP文件的扩展名
php{Ver}:安装PHP包
php{Ver}-php-pecl-memcached:x86_64:使用Memcached的扩展缓存守护进程
php{Ver}-php-zstd:x86_64: Zstandard扩展名
php{Ver}-php-pecl-json-post:JSON POST处理程序
php{Ver}-php-pecl-couchbase2:Couchbase服务器PHP扩展
php{Ver}-php-pecl-krb5-devel:Kerberos扩展开发人员文件(头)
php{Ver}-php-pecl-memcache:x86_64:使用Memcached的扩展缓存守护进程
php{Ver}-php-pecl-xattr:扩展属性
php{Ver}-php-pecl-svn:x86_64: Subversion版本的PHP绑定控制系统
php{Ver}-php-pecl-seaslog:一个有效、快速、稳定的日志 PHP扩展
php{Ver}-php-pecl-protobuf:序列化结构化的机制数据
php{Ver}-php-enchant:增强PHP的拼写扩展应用程序
php{Ver}-php-pecl-mogilefs:要与之通信的PHP客户端库 MogileFS存储
php{Ver}-php-phalcon4:Phalcon框架
php{Ver}-php-pecl-xmldiff:x86_64: XML差异和合并
php{Ver}-php-pecl-trader:为贸易商提供技术分析
php{Ver}-php-litespeed:LiteSpeed Web服务器PHP支持
php{Ver}-php-pecl-rpminfo:x86_64: RPM信息
php{Ver}-php-pecl-uopz:x86_64: Zend的用户操作
php{Ver}-php-pecl-gnupg:x86_64: gpgme库的包装
php{Ver}-php-pecl-vld:x86_64:转储PHP的内部表示脚本
php{Ver}-php-pecl-apcu:APC用户缓存
php{Ver}-php-maxminddb:MaxMind DB Reader扩展
php{Ver}-php-embedded:用于嵌入应用程序的PHP库
php{Ver}-php-pecl-wddx:Web分布式数据交换
php{Ver}-php-pecl-seasclick:一个Yandex ClickHouse客户端驱动 PHP扩展
php{Ver}-php-pecl-ip2location:获取an的地理位置信息IP地址
php{Ver}-php-pecl-xdiff:文件差异/补丁
php{Ver}-php-pecl-psr:PSR接口
php{Ver}-build:基本的构建配置
php{Ver}-php-pgsql:一个用于PHP的PostgreSQL数据库模块
php{Ver}-php-json:x86_64: PHP的JavaScript对象符号扩展
php{Ver}-php-pecl-yaconf-devel:php{Ver}-php-pecl-yaconf developer files (header)
php{Ver}-php-pecl-scoutapm:本地扩展组件 ScoutAPM的PHP代理
php{Ver}-php-pecl-druid:一个PHP的德鲁伊驱动
php{Ver}-php-mysqlnd:x86_64:用于使用MySQL的PHP应用程序的模块数据库
php{Ver}-php-pecl-xxtea:XXTEA加密算法扩展PHP
php{Ver}-php-smbclient:libsmbclient的PHP包装
php{Ver}-php-pecl-mysql:MySQL数据库访问函数
php{Ver}-php-pecl-http:扩展的HTTP支持
php{Ver}-php-pecl-recode:A module for PHP applications for using the recode library
php{Ver}-php-odbc:x86_64:用于使用ODBC的PHP应用程序的模块数据库
php{Ver}-php-tidy:标准PHP模块提供了tidy库支持
php{Ver}-php-xmlrpc:的PHP应用程序模块xml - rpc协议
php{Ver}-php-gd:用于PHP应用程序使用gd的模块图形库
php{Ver}-php-pecl-uuid:通用唯一标识符扩展对于PHP
php{Ver}-php-pecl-lua:嵌入式lua解释器
php{Ver}-php-intl:x86_64: PHP国际化扩展应用程序
php{Ver}-php-pecl-datadog-trace:APM和分布式跟踪PHP
php{Ver}-php-ffi:外部函数接口
php{Ver}-php-pecl-timecop:x86_64:时间旅行和冻结扩展
php{Ver}-php-pecl-mailparse:用于解析和的PHP PECL包处理电子邮件消息
php{Ver}-php-pecl-skywalking:x86_64: Apache的PHP工具代理人行天桥
php{Ver}-php-sqlsrv:x86_64:用于SQL Server的PHP Microsoft驱动程序
php{Ver}-php-pecl-memprof:x86_64:内存使用分析器
php{Ver}-php-zephir-parser:x86_64: Zephir解析器扩展
php{Ver}-php-bcmath:用于PHP应用程序的模块bcmath库
php{Ver}-php-pecl-runkit7:为了这些你…不应该…无论如何我一直在做……但是肯定做的!
php{Ver}-scldevel:x86_64:打包php{Ver}的开发文件
php{Ver}-php-pecl-geoip:将IP地址映射到的扩展名地理位置
php{Ver}-php-pinba:x86_64: Pinba统计服务器的客户端扩展
php{Ver}-php-pecl-dbase:dBase数据库文件访问函数
php{Ver}-php-pecl-ssh2:x86_64: libssh2库的绑定
php{Ver}-php-pecl-pq:PostgreSQL客户端库(libpq)绑定
php{Ver}-php-pecl-pdflib:生成PDF文件的包
php{Ver}-php-pecl-radius:Radius客户端库
php{Ver}-php-pecl-eio:提供libeio库的接口
php{Ver}-php-pecl-sphinx:Sphinx SQL全文的PECL扩展搜索引擎
php{Ver}-php-pecl-mustache:Mustache模板语言
php{Ver}-php-pecl-yaconf:x86_64:另一个配置容器
php{Ver}-php-ast:抽象语法树
php{Ver}-php-pecl-gearman:PHP包装器到libgearman
php{Ver}-php-pecl-hdr-histogram:x86_64: C语言的PHP扩展包装hdrhistogram API
php{Ver}-php-pdo-dblib:x86_64: PDO驱动程序，用于Microsoft SQL Server和Sybase数据库
php{Ver}-php-pecl-scrypt:Scrypt散列函数
php{Ver}-php-pecl-ahocorasick:有效的Aho-Corasick字符串模式匹配算法
php{Ver}-php-pecl-raphf-devel:php{Ver}-php-pecl-raphf developer files (header)
php{Ver}-php-pecl-bitset:位集库
php{Ver}-php-pecl-mcrypt:x86_64: libmcrypt库的绑定
php{Ver}-php-mbstring:一个用于PHP应用程序的模块多字节字符串处理
php{Ver}-php-pdo:一个用于PHP的数据库访问抽象模块应用程序
php{Ver}-php-pecl-gmagick:的包装器GraphicsMagick库
php{Ver}-php-pecl-amqp:与任何AMQP兼容的服务器通信
php{Ver}-php-libvirt-doc:noarch: php-libvirt文件
php{Ver}-php-pecl-mosquitto:libmosquito - to的扩展
php{Ver}-php-pecl-leveldb:LevelDB PHP绑定
php{Ver}-php-pecl-lzf:x86_64:处理LZF de/压缩的扩展
php{Ver}-php-pecl-base58:用base58编码和解码数据
php{Ver}-php-pecl-inotify:x86_64: Inotify
php{Ver}-php-pecl-crypto:OpenSSL密码库的包装器
php{Ver}-php-imap:x86_64:用于使用IMAP的PHP应用程序的模块
php{Ver}-php-pecl-yaml:x86_64: yaml的PHP绑定
php{Ver}-php-pecl-imagick-devel:imagick扩展开发人员文件(头)
php{Ver}-php-pecl-solr2:Apache Solr的API定向对象
php{Ver}-php-horde-horde-lz4:Horde LZ4压缩扩展
php{Ver}-php-ioncube-loader:Loader for ionCube Encoded Files with ionCube 24 support
php{Ver}-php-snappy:PHP的Snappy扩展
php{Ver}-php-pecl-hrtime:x86_64:高分辨率定时
php{Ver}-php-pecl-raphf:资源和持久句柄工厂
php{Ver}-php-pecl-http-devel:x86_64:扩展HTTP支持开发人员文件(头)
php{Ver}-php-pecl-stomp:Stomp客户端扩展
php{Ver}-php-pecl-uv:Libuv包装器
php{Ver}-php-pecl-luasandbox:带有限制和安全的Lua解释器环境
php{Ver}-php-pecl-msgpack:用于与MessagePack通信的API序列化
php{Ver}-php-pecl-mysql-xdevapi:MySQL数据库访问函数
php{Ver}-php-pecl-event:提供libevent库的接口
php{Ver}-php-dbg:交互式PHP调试器
php{Ver}-php-pecl-msgpack-devel:MessagePack开发人员文件(头)
php{Ver}-php-pecl-env:加载环境变量
php{Ver}-php-pecl-ds:x86_64: PHP的数据结构
php{Ver}-php-dba:一个用于PHP的数据库抽象层模块应用程序
php{Ver}-php-pecl-gender:x86_64:性别扩展
php{Ver}-php-pecl-translit:将非拉丁字符音译设置为拉丁文
php{Ver}-php-wkhtmltox:HTML转换器
php{Ver}-php-pecl-vips:x86_64:与libvip接口的PHP扩展
php{Ver}-unit-php:用于NGINX单元的PHP模块
php{Ver}-php-pecl-opencensus:一个stats集合和分布式跟踪框架
php{Ver}-php-snmp:一个用于PHP应用程序查询的模块SNMP-managed设备
php{Ver}-php-ldap:x86_64:用于使用LDAP的PHP应用程序的模块
php{Ver}-php-opcache:x86_64: Zend OPcache
php{Ver}-php-pecl-mysqlnd-azure:x86_64: mysqlnd的重定向插件
php{Ver}-php-pecl-dio:直接I/O函数
php{Ver}-php-pecl-geospatial:PHP扩展来处理公共地理空间功能
php{Ver}-php-pecl-ev:提供libev库的接口
php{Ver}-php-pecl-igbinary-devel:Igbinary开发人员文件(头)
  ```
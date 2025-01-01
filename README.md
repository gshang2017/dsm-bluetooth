## 群晖nas自用：

### 参考文章:

[https://github.com/kcsoft/synology-bluetooth](https://github.com/kcsoft/synology-bluetooth)                        
[https://blog.csdn.net/m0_72359111/article/details/142472320](https://blog.csdn.net/m0_72359111/article/details/142472320)             
[https://www.cnblogs.com/wanglouxiaozi/p/17832303.html](https://www.cnblogs.com/wanglouxiaozi/p/17832303.html)

### 版本：

* rtl8761b版加了补丁，用来驱动淘宝上买的杂牌双天线版蓝牙。

### 使用说明：

1. 变量

    |变量名|说明|
    |:-:|:-|
    |LINUX_URL|[群晖内核linux文件下载地址](https://archive.synology.cn/download/ToolChain/Synology%20NAS%20GPL%20Source)|
    |TOOLCHAIN_URL|[群晖toolchain文件下载地址](https://archive.synology.cn/download/ToolChain/toolchain)|
    |MODEL|群晖架构,例如apollolake|
    |ENABLE_RTL8761B_PATCH|(true\|false)rtl8761b(linux-4.4.x)补丁|

2. 自编译(ubuntu:22.04)

       export LINUX_URL="https://global.synologydownload.com/download/ToolChain/Synology%20NAS%20GPL%20Source/7.2-64570/apollolake/linux-4.4.x.txz"
       export TOOLCHAIN_URL="https://global.synologydownload.com/download/ToolChain/toolchain/7.2-72746/Intel%20x86%20Linux%204.4.180%20%28Apollolake%29/apollolake-gcc1220_glibc236_x86_64-GPL.txz"
       export MODEL=apollolake
       export ENABLE_RTL8761B_PATCH=false
       cd ./dsm-bluetooth && sudo chmod +x ./dsm-bluetooth.sh && sudo -E ./dsm-bluetooth.sh

3. 安装蓝牙文件

       sudo chmod +x ./install.sh
       sudo ./install.sh

4. 删除蓝牙文件

       sudo chmod +x ./uninstall.sh
       sudo ./uninstall.sh

5. 加载蓝牙内核驱动(开机启动需添加至群晖任务计划 新增-触发任务-任务设置-运行命令)

       sudo /usr/local/etc/rc.d/bluetooth-modules.sh start

6. 停止蓝牙内核驱动

       sudo /usr/local/etc/rc.d/bluetooth-modules.sh stop

+++
title = 'Linux重装'
date = 2024-03-26T18:28:01+08:00
draft = false
+++
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403191526421.jpg)
# Window与Linux双系统安装与卸载Linux

*如果你事先在window上安装的ubuntu,但是因为种种原因需要重装，那么你需要先卸载装在你电脑上的ubuntu系统才能安装新的Ubuntu*

*重装unbuntu记得先保存好ubuntu想保存的文件*

## Ubuntu卸载

### 删除ubuntu所在卷

进入windows系统，右键此电脑-管理-磁盘管理-删除ubuntu所在的卷，使这些区域成为“可用空间”

### 删除unbuntu EFI分区

Win + R 输入cmd打开终端，输入 diskpart 进入磁盘工具

输入 list disk 查看磁盘，输入 select disk 1 （我的Ubuntu EFI分区在磁盘1，根据自己的情况选择）

输入 list partition ，输入 select partition * （*为Ubuntu EFI分区号）

### 删除Ubuntu系统启动项

Win + R 输入cmd打开终端，输入 diskpart 进入磁盘工具

输入 list disk 查看磁盘，输入 select disk 1

输入 list partition ，输入 select partition * （*为Windows EFI分区，一般为260M）

输入 assign letter=J（分配盘符）

管理员模式打开记事本，记事本选择文件-打开-选中磁盘J

打开 EFI 文件夹，删除Ubuntu文件夹

返回 Distpart 界面，输入 remove letter=J

## 磁盘分区（如果你是第一次装Ubuntu）
1.打开计算机管理
2.找到磁盘管理
3.选择你要压缩的盘，**你压缩掉的空间将作为新系统的空间**
4.右键打开你要压缩的盘符，点击压缩卷
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403182047551.png)
![](https://raw.githubusercontent.com/a-b-ab/picture/main/Picgo202403182047587.png)

## 安装ubuntu系统
**强烈建议安装最新lts版本，我写这篇博客时是22.04版**
*我就是因为第一次装的是18.04版所以才重装的，QAQ*

### 下载Linux镜像
1.下载 Ubuntu 镜像，这里可以去官方下载，但是官方在国外，默认外网链接可能网速有点小慢。（科技玩家例外）
更好的选择是国内的资源镜像网站，比如说清华大学开源软件镜像站

清华大学开源软件镜像站 https://mirrors.tuna.tsinghua.edu.cn/

### 准备u盘刻盘工具
我用的是UltralSO

下载后打开，找到你下载的镜像文件，找到后，点击右上角的启动->写入硬盘映像

*写入时记得插入u盘，这个u盘将作为启动盘*
*写入时，这个u盘的数据全会被格式化，谨慎操作*

然后点击写入就可以了

### 开机引导界面
将写好的映像文件的U盘插入你需要的电脑，在开始时按f12，本人用的是联想，不同电脑可能不同，正常都是f12

在引导界面可以看到几个选项，选择你的u盘作为启动项，反正不是window和network就是了

启动后你会进入系统选择界面，使用方向键选择 ubuntu 后回车就进入了 Ubuntu 的安装引导界面。在侧边栏中选择系统语言，English、Chinese都可，看自己喜好，然后点击 Install Ubuntu 进入安装，选择安装方式，选择正常安装就行，会默认安装火狐浏览器等软件。或者选择最小安装的话可以在安装完成后自行安装需要的软件，两种方式影响不大。下面的安装第三方软件选项也可以选上，也可以不选，后面再根据需要手动安装。我这里就只选择了正常安装，然后点击继续，在安装类型选择时，建议自己手动分区，说一下分区情况吧，我找了大部分教程都是分为四个区：

#### 分区方案
/boot : 1G（最好）  主分区。系统的boot启动引导项安装位置

/  : 随意（尽量大）    主分区。根目录，所有目录的根节点，其下包含很多子目录，如/usr  /tmp等

/home :  自定义（尽量大，一般最后分）   逻辑分区。一般放置自己的数据

swap : 16G   逻辑分区。交换空间，一般是物理内存的1~2倍就行了

具体操作，首先找到 free space 空间，如下，选中该空间，点击左下角的加号+，进行内存分配

安装后->选择地区（上海或香港都可以，我选的是上海）->设置账户密码->重启->输入密码，ok

*我和同学在重启时都出现，黑屏跳一堆数据的情况，我们当时都很慌，但是我们最后强制关机重启后，发现没有大问题，起码我们没发现问题*

以后你每次开机时都可以选择windo和Linux之一的系统进行启动
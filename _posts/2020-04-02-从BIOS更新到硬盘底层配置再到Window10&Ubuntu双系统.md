---
layout:     post
title:      最详细的重装电脑记录
subtitle:   从BIOS更新到硬盘底层配置再到Window10&Ubuntu双系统
date:       2020-04-02
author:     LXY
header-img: img/post-bg-desk.jpg
catalog: true
tags:
    - 装机
    - BIOS
    - Linux
---

**写在前面**：

- 本博客意在记录我从更新BIOS到分配硬盘到Windows10&Ubuntu18.04双系统的全过程。曾经遇到win10蓝屏啊，崩溃啊，双系统不稳定啊之类的问题，其实是底层没做好。我之前由于实验动了BIOS，所以这次大重装也一起更新了。笔者电脑是联想y7000，显卡GTX1650（这台电脑网卡和Ubuntu18.04之前出问题，需要改个环境变量，18.04网卡好了但又和显卡出问题，之后会提到，如果没遇到相关问题请自行略过）。==BIOS部分高风险，这东西坏了电脑就真成砖了，然而只要BIOS没坏，一切都可以重来。== 由于截屏十分麻烦，本文图片都是手机拍照，糊到不至于，影响可能还是有一点点，凑活一下吧。
- 强调：==数据无价，做好备份！==
- 本博客为几篇不同的博客的合并版，其他内容参照以下连接：(暂未更新相关博客）
	- BIOS如何更新，回刷：
	- 从底层分区开始做一个干净的Windows10：
	- 如何做一个稳定的Windows10&Ubuntu双系统：
	- 如何利用图形界面解决Ubuntu启动时乱码，nvidia显卡无法驱动的问题（基本不用命令行）：

# 从BIOS更新到硬盘底层配置再到Window10&Ubuntu双系统（BIOS更新部分可忽略）
---
## 前期准备
- 首先需要两个U盘，一个做成老毛桃（或者winpe），另外一个分别做win10和Ubuntu的镜像。~~【什么？老毛桃有广告给电脑装插件？在**支持我们**里面有关闭的地方哦】~~ （ps：老毛桃或winpe是做底层必须的，这个去官网直接下载，做起来很容易的）
- 需要一台电脑
- 需要一天时间~~毕竟我也不好说你在哪里会踩坑~~

附网址：
winpe：  http://www.wepe.com.cn/
老毛桃： http://www.laotiaomao.top/
我是用很久以前版本的做的老毛桃，这里应该大同小异吧。winpe是有段时间没维护了，但使用不成问题，而且无广告。

---
## 1.BIOS更新
风险警告：刷错可能成砖！！！
### 1.1准备工作
首先先去你电脑的官方网站找到BIOS更新的软件。我的是联想的电脑，就去官方找。点开官方，点击服务，输入设备编号即可查找。 ==**一定要输入设备编号或者型号，这样才能找到正确的BIOS，刷了别的机子的BIOS可能就成砖了**==![官网的BIOS](https://img-blog.csdnimg.cn/20200401233120326.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
直接点BIOS升级程序几个字可以看到以前的版本。
### 1.2开始搞事
==确保电脑连了**稳定的**电源==
==确保电脑连了**稳定的**电源==
==确保电脑连了**稳定的**电源==
   `【否则会成砖】`

#### 1.2.1调整BIOS
如果是更新BIOS可忽略，如果是回刷可参考。
关机，重启，F2进入BIOS（不同电脑可能不一样）。进入第二个菜单，`BIOS Back Flash`改为Enabled，这个意思是允许回刷，由于我之前刷过，所以当前版本也算上一个版本，如果BIOS不开这个是不允许回刷的，如果是更新，自动忽略这一步
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200401233658548.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
保存退出BIOS
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200401234049394.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
#### 1.2.2 运行刷BIOS的程序
进入Windows，打开之前官网下载的程序。一路点下去
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200401234433732.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200401234449509.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200401234702205.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
这个确定点下去之后就开始了激动人心的刷BIOS过程，全程自动，千万不要拿电脑干别的事情，千万不要拔电源（刷BIOS必须要插电源，轻则程序发现提醒你插，重则成砖）。让电脑自己安静工作以免==成砖==。配一张吓人的图片。刷完了会自动重启。还是很简单的。到此大功告成。
![配一张恐怖的图片](https://img-blog.csdnimg.cn/20200401234944588.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
秀一下最新的BIOS版本（至少写的时候是最新的）
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040211213653.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)

---
## 2.Windows10
### 2.1.前期准备
#### 2.1.1在BIOS中查询一个数据
Boot Mode: UEFI

记着后边要用。![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402002754458.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
#### 2.1.2去官网上下载制作工具。
一定要去官网上下载，做出来的系统纯净到比你电脑买来还干净。当时看到那界面真是干净到“开机只见回收站”。但是有点难找。我帮你指路。
打开官网
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402000203141.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
拉到最下面找到`下载中心`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402000250637.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
点击`Windows 10 帮助`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402000321286.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
在`安装和升级`里面找到`重新安装windows10 `
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402000409100.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
你会得到一篇教程，仔细阅读，你就能基本掌握如何安装win10.
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040200054031.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
我是使用安装介质来做的，细读这里，然后拿出准备好的干净U盘做一个启动盘，基本上用微软的软件确定到底，这里就不在赘述了。微软官网写的十分详尽。![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402000636422.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
### 2.2清理磁盘
关机，插上winpe的U盘，重启，狂按F12进入boot菜单（不同电脑可能按不同的按键）。选中USB启动。（大家内容可能不一样，我这里是之前装的Ubuntu引导还在这里没处理，反正通过USB三个字母或者U盘名字来判断，我这是闪迪SanDisk）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402001256878.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)

找到这玩意，diskgenius。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402001521579.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
打开后可以看见你的分区，谨慎操作，这里面动的都是底层。啥权限都会失效的，没有保护。这是我目前的状况（也是双系统做好后的状态，为了博客取材我重来了一遍）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402001805483.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
选中C盘，然后点击删除分区（贼刺激，删了C盘）
![](https://img-blog.csdnimg.cn/20200402001853329.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402001910316.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
如法炮制把其他的都删了，这样底层才干净。有些电脑最后有1000M用于一键恢复，就是duo一下恢复的winre可以保留。（我是觉得用winpe可以做镜像备份，镜像备份还原系统更方便也更快，留着无用，就给他删了）还有些电脑最前面有个500M的win10预留的空间，那个是win10装机时，是个空硬盘然后微软装系统的程序预留的，感觉并没有什么用，~~大概~~。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402002142717.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
点击左上角保存更改，确定。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402002240963.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
这个时候你的电脑硬盘是彻底做干净了。啥都没有，这个时候重启特别好玩，没有引导就像个砖一样，没错，没装系统的原始状态，只有BIOS在工作，非常干净，啥都没有，从零开始。无论你出什么问题 ~~（物理损坏除外）~~ ，这样搞，都可以洗白硬盘，然后从零开始。

顺便一提，如果刷过BIOS，这个时候进入BIOS可以看到干净的很。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402003120222.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
### 建立分区
首先点击`分区-建立ESP/MSR分区`。这两个分区是windows为了支持更大的硬盘（2T及以上）而需要的，以前的win7之类的就没有这些分区，一上来就是C。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040209481479.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
使用默认配置即可。这一幅图中的提示就解释了原因，所谓电脑采用UEFI系统，就是之前准备工作在BIOS里面查询的内容。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402095028962.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
点击确认，自动生成两个盘，然后就可以分其他盘了，`选中空闲部分`，`点击新建分区`。我512的硬盘，分了120GB的C，300GB的D，剩下的50GB的样子是留给Ubuntu的。C盘一般100GB，但就我个人使用使用而言100不太够，~~毕竟不喜欢看他变红~~。这个分区看自己。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402095545770.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
点击右上角保存更改，会提示你格式化。确认即可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/202004021000276.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
然后底层分区什么的就做的非常干净了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402100403464.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
### 2.3安装win10
关机，拔出winpe的U盘（这里拔出只是防止启动时搞混），然后插上做好的win10启动盘，就是用微软官网程序做的那个。
然后重启，狂按F12进入boot菜单，选择USB启动，然后会进入win10的安装界面。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402100949939.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
语言什么当然是中文，~~英语大佬可以尝试英文~~。点击下一步，会让你激活Windows。因为我电脑本身是Windows10家庭版，而这次重装是装的专业版（从其他机器上撕下来的序列号,有可能后期装好后激活失败，不过我运气好能激活），所以需要输入序列号。如果你下的版本和你原来是一样的，比如你本来是正版的家庭版，然后做的是家庭版的安装U盘，那么直接点`我没有激活密钥`，然后他会识别你的硬件等，到时候会自动激活，微软这点做的还是很好的。如果后期激活失败，打微软的客服，客服小姐姐会收集你的机器信息，从微软找到序列号，然后手把手教你如何激活。客服小姐姐，手把手哦~， ~~当然技术肥宅客服也不排除~~

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040210213645.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
这里输入密钥之后可能会卡一会儿，问题不大，过了之后选择自定义安装。保留了文件、设置、应用程序是升级用的，这里底层已经做干净了，用不着了。~~保留了文件、设置、应用程序那叫重装？系统都不干净~~
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040210222888.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
然后是选择在哪里安装Windows，当然是之前分的120GB咯~  选中之后点击下一步。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402102508557.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
开始安装。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040210261547.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
等一段时间，好了，大功告成。
### 2.4Windows10基本设置（即拿到新电脑之后做啥）
区域：选择中国。~~外国人或者有志向在其他语言发展的自动选择其他的~~
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402102933422.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
连接网络这里有点技巧，连了网会叫你登陆微软账号什么的，账号验证慢的要死，~~毕竟服务器在地球的另一边~~，而且对密码有复杂度的限制，还有一堆微软服务，麻烦。现在的win10连了网也可以绕过账号验证哪里，但是我每次都不知道怎么乱七八糟的绕过去，~~好像多次输错密码？~~ 没有直接的按钮可以让你跳过登录账户，反正麻烦。这个地方点击左下角我没有Internet连接可以绕过去。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402103604872.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
然后弹出一个窗口勾引我联网，点左下角，不理他。
![](https://img-blog.csdnimg.cn/20200402103634703.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
然后随便给个名字。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402103658778.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
服务器在地球另一端，慢的要死，而且感觉这些服务用不到，点否。（想用这些服务的可以点是。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402103824594.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
隐私设置，~~不能让微软知道我的隐私~~，全部点掉。当然也可不点。点击接受。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402103921407.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
好了，到此已经完成基本装机√。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402104024581.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
### 2.5驱动安装
这里真的说一下，Windows的驱动十分良心，不要搞什么乱七八糟的驱动精灵，甚至联想自己的驱动都配置的乱七八糟的。可以在设备管理器中看到，很多硬件都有感叹号，说明没驱动起来。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402104434982.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
连上网，进入设置，在更新和安全里找到Windows更新，然后点击检查更新。下载安装什么的可能比较慢，有时会提醒你重启，可以当场重启，也可以都下完了再重启。会有个别更新失败，重启后在进来点检查更新，直到全部更新完。在电脑更新完成之前==不建议进行任何操作，包括安装chrome之类的==  ，免得说不清楚什么软件把底层搞乱了。时间有点长，耐心点。包括nvidia显卡的驱动，win10都会安排的妥妥当当的，完全不需要自己弄。什么驱动没安装好，什么系统出错，要么是底层搭的不好，要么是阻碍了这些更新。~~（什么，最新的win10更新有蓝屏bug？底层做好，蓝屏，不存在的）~~ 
更新完了，就可以干自己的事情了。大功告成。

---
## 3.Ubuntu双系统安装
### 3.1前期准备
去官网下载iOS镜像，建议找到中文官网，服务器在国内下载更快哦~（这里先以18.04.03做示范，这个版本不会出现显卡驱动问题）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402114819918.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402110314327.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
#### 3.1.1制作启动盘
这里有多个选择
- 用Ubuntu官方的方式做启动盘
- 用UltraIOS制作启动盘，可以在Windows10下下载该软件，也可直接用winpe中自带的。

*我这里使用winpe去做他*
==winpe下一切操作需要谨慎==
关机，插上winpe的U盘，然后重启，狂按F12进入boot（不同电脑方式可能不同），选择U盘启动。进入winpe之后插入另一个U盘。然后找到UltraIOS。点击左上角 文件-打开
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402111154918.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
找到IOS文件，选择他。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402111309351.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
在启动菜单中找到==写入硬盘映像== 注意，一定要是硬盘！
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402111530548.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
默认配置即可，注意，图中那个位置，若不是USB-HDD+就改成这个，这个成功率较高。点击写入。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402111837610.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
选“是”。![。](https://img-blog.csdnimg.cn/20200402111902130.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
自动写入。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402111930683.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
写完过后返回，然后关机。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402111948369.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
#### 3.1.2附一张此时硬盘分区
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040212025078.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
### 3.2 修改BIOS
在Security里面找到Secure Boot 改为Disabled。这里是因为电脑一般为了安全，稳定，不允许双系统，所以有个安全选项，关了即可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040211231394.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040211240853.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
保存退出。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402112537630.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
### 3.3安装Ubuntu18.04.3
重启时进入boot，可以看到第一个是进入Windows。我们选择U盘启动，是Ubuntu的启动盘，不是winpe哈。（图上，我换了个U盘）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402112738311.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
此处若出现下图状况，是nvidia显卡驱动问题，参考后文“Ubuntu显卡驱动问题——Y7000避坑指南”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402115453431.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)

进入后直接Enter可以进入Ubuntu livecd（体验版Ubuntu），左上角那个就是安装文件。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402112909293.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
双击开始安装。一路点下去。
![在这里插入图片描述](https://img-blog.csdnimg.cn/202004021129262.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
在这个地方，安装类型选择其他。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402113016198.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
然后就开始分区，这里的空闲是之前装win10之前用磁盘工具分剩下的。点击右下角的加号。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402113122547.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
这里我分了三个区。
- /boot分区，1024MB
- 交换分区，8192MB（关于这个，传统上是分内存大小的两倍，其作用是在内存不够用时分一部分到硬盘上，不过这是以前，或者是现在的单片机内存不够的情况下才有用。由于对计算机理解有限，折中分了内存的一倍，8个G，其实我觉得4G就够了，算了懒得再装一遍）
- 主分区，剩下空间。当然你也可以像win一样分CD盘，但是我剩下空间只剩五十来个G，就不分了。
以下的图片是对应的配置，分区类型，用于要自己改，按照图片即可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402113952375.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402114017165.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402114026596.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
== 正确选择安装启动引导器的设备==
这里挂到你的\boot分区，这里很重要，不要搞错，错了又是“砖”，或者把底层装乱。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402114338556.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
然后就等。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402114445488.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
完了重启即可
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040211445655.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
开机会进入grub界面，第一个是进Ubuntu，第三个进Windows。更改默认选项，默认时间，grub美化，移步百度。
用winpe工具来看，可以看见底层十分舒适。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402114908265.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
## 4.Ubuntu显卡驱动问题——Y7000避坑指南
我这Y7000不仅网卡不行，显卡也出问题。
### 4.1安装Ubuntu18.04.4
U盘启动Ubuntu的U盘，然后在这个界面按一下`e`，注意，一下，否则会很好玩。（grub最下面有提示）
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040211562147.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
然后进入这个界面
修改那三个---，改为nomodeset。（建议移动光标一下一下点~~长按上下左右会出现很好玩的事情~~）（nomodeset：意思是不加载硬件）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402115755630.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402115939263.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
之后按F10正常启动。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402120057790.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
像之前一样安装。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402120121623.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
### 4.2安装ividia显卡驱动（图形界面，没有命令）

第一步先打脸。。。
进入grub时及时点`e`然后进入这个界面，将红色部分删除。~~（长按退格会很神奇，不要尝试）~~
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402120616227.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
将ro之后改成`nouveau.modeset=0`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402120740374.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
按F10正常启动。
可以看见WiFi正常了，我们把它连上。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402120851439.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
进入所有程序，点这个换源。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040212103464.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121042924.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
一般点右上角那个选项自动寻找最快的源。选择服务器。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121109422.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
点击关闭，然后点击重新载入。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121133848.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
装显卡驱动前更新一下其他驱动。
- 两行命令更新软件包（可以跳过这两行命令）
`sudo apt-get update`
`sudo apt-get upgrade`
- 这个更新完之后，点击这个来更新。
（当然也可以直接点击这个来更新。）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121252528.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
点击，稍后重启。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121441396.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
在所有程序中找到Ubuntu软件。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040212163377.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
点击附加驱动，稍微等一会儿。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121657535.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
然后如图找到显卡驱动，然后点击应用更改。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121718271.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
之后重新启动。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121751134.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
在从grub进去就不用按e了，一切正常，大功告成。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200402121835914.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l0TGFuY2U=,size_16,color_FFFFFF,t_70)
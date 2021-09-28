---
layout:     post
title:      Netch使用指南(190627)
date:       2019-06-24 19:00:00
author:     "冰灵"
categories:
    - 演示
tags:
    - 教程
    - 游戏加速器
thumbnail: "https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/Netch_guide/cartel_07.jpg"
---
>题图来源<escape><a name = "ref_1_s"><a href="#ref_1_d"><sup>[1]</sup></a></a></escape>
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。
>标题后面括号里的日期指的是最后更新日期，头像旁边的日期是最初发布日期。

<escape><font size=4>目录</font></escape>

1. [简介](#简介)
2. [关于软件](#关于软件)
3. [使用方法](#使用方法)
   - 3.1 [新建代理配置](#新建代理配置)
   - 3.2 [快速创建模式](#快速创建模式)
   - 3.3 [扫描](#扫描)
   - 3.4 [启动](#启动)
4. [线路选择](#线路选择)
5. [中二选择](#中二选择)
6. [注释](#注释)

### 简介

Netch是一款开源的游戏加速工具，不同于SSTap那样需要通过添加规则来实现黑名单代理，Netch原理更类似[Sockscap64](https://www.sockscap64.com/homepage/)，通过扫描游戏目录获得需要代理的进程名进行代理。

与此同时Netch避免了SSTap的NAT问题<escape><a name = "ref_2_s"><a href="#ref_2_d"><sup>[2]</sup></a></a><a name = "ref_3_s"><a href="#ref_3_d"><sup>[3]</sup></a></a></escape>，使用SSTap加速部分P2P联机，对NAT类型有要求的游戏时，可能会因为NAT类型严格遇到无法加入联机，或者其他影响游戏体验的情况。

### 关于软件

- [Netch版本发布频道(Telegram Channel)](https://t.me/NetchXChannel)
- [github仓库](https://github.com/NetchX/Netch): netchx/Netch: Game acceleration tool. Support Socks5, Shadowsocks, ShadowsocksR, V2Ray protocol. UDP NAT FullCone
  - 感觉有用别忘了素质三连(Star & Watch & Fork)
- [github发布](https://github.com/netchx/Netch/releases)
- [Netch游戏加速工具讨论群(Telegram Group)](https://t.me/NetchX)
  - 有问题可以进群讨论

### 使用方法

- 现在软件还处在早期开发阶段，可能后续版本会发生很大变化，操作仅供参考。

#### 新建代理配置

当前版本已添加配置编辑功能，根据自己的情况，使用订阅或者别的方法添加代理配置，我这里使用的是剪贴板导入。

如果你想使用的代理工具目前Netch还不支持，可以通过socks5代理进行中转，也就是让Netch访问你的代理工具提供的socks5代理。

<escape><div title="剪贴板导入.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/Netch_guide/2019-06-24_210438.png" height="80%" width="80%"></div><div align="middle">剪贴板导入.jpg</div></escape>

~~如果你发现你的程序没我截图的看起来清晰，可以右键Netch.exe-属性-兼容性-更改高DPI设置-替代高DPI缩放执行-系统(增强)。~~

#### 快速创建模式

如果你的游戏的模式已经被收录，也可以考虑直接使用已收录的模式。所有模式的文件，都在 `./mode/` 文件夹下，如果你需要多个模式的合并文件，可以使用记事本将其打开，将多个文件合并。

<escape><div title="点击快速创建模式.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/Netch_guide/2019-06-24 211537.png" height="80%" width="80%"></div><div align="middle">点击快速创建模式.jpg</div></escape>

~~图中绿色的0是因为我使用了本地中转，Netch内建的ping功能未能检测出真实的延迟数据。~~

ping的值未必准确，因为这只是你本地到代理服务器而非游戏服务器的延迟。

如果你的游戏的模式没被收录，可以看接下来的扫描步骤来手动创建模式。

接着点击菜单栏上的快速创建模式。

#### 扫描

在弹出的窗口中点击扫描。

<escape><div title="扫描.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/Netch_guide/2019-06-24 211842.png" height="50%" width="50%"></div><div align="middle">扫描.jpg</div></escape>

选择你要加速的游戏的安装路径，根据游戏不同，可能需要选择多个不同的目录进行扫描，参见[萌鹰的Netch教程](https://www.eaglemoe.com/archives/142)(包括GTAOL和R6S的配置方法)。

>4. 选定GTA5游戏目录，点击确定，软件会自动扫描目录下的exe程式并填写进去。
>5. 再次点击扫描，选择socialclub的安装地址（一般为C:\Program Files\Rockstar Games\Social Club），点击确定，点击保存。
>
>注意：加入游戏时请不要忘记加入社交组件，比如说GTA不要忘记socialclub，彩虹六号不要忘记uplay。

这里以战争雷霆为例，只需添加战争雷霆游戏根目录即可，当前版本暂时不支持输入目录路径进行扫描。

<escape><div title="选择路径.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/Netch_guide/2019-06-24 212036.png" height="50%" width="50%"></div><div align="middle">选择路径.jpg</div></escape>

扫描时可能需要稍等片刻，扫描后记得填写备注，如果需要添加单个程序，也可以在添加按钮左侧的编辑栏中手动输入并添加。

之后点保存进行保存。

<escape><div title="保存.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/Netch_guide/2019-06-24 212837.png" height="50%" width="50%"></div><div align="middle">保存.jpg</div></escape>

#### 启动

最后确认服务器一栏和模式一栏均为之前自己添加并需要使用的，没问题后点击启动即可。

<escape><div title="启动.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/Netch_guide/2019-06-24 213121.png" height="80%" width="80%"></div><div align="middle">启动.jpg</div></escape>

启动后，你再去游戏根目录或者别的启动器如Steam，Uplay启动游戏即可。此时游戏就已经被代理了。

如果在Netch启动前就启动了游戏，建议重启游戏。

如果需要Steam，Uplay等启动器也被代理，参照前面的方式对Steam，Uplay根目录也进行扫描即可。

### 线路选择

普通人可以入手[n3ro](https://n3ro.io/)的线路(不负责推荐)，根据[sabre大佬的科普](https://t.me/sabershome/197)，iplc的线路较为稳定。

### 中二选择

打算使用自己租赁的服务器加速游戏的中二人士可以了解一下，多种网络工具配合使用，战公网。

[UDPSpeeder+Udp2raw使用教程](https://www.moerats.com/archives/662/)

### 注释

点击上箭头字符可返回原位置，方括号中的数字表示引用的次序。
<escape><a name = "ref_1_d"><a href = "#ref_1_d">[1]</a></a>&nbsp;<a href = "#ref_1_s">&nbsp;↑&nbsp;</a>&nbsp;<a href = "https://photos.google.com/share/AF1QipPjwI4529KHV1S3r6ZosohpLXr6TRtNtqUtyJljbGd3rjDrCQla6tqB3spF_8QaUg/photo/AF1QipPBPhru6gZ2SlZ7dYBeZDAUTyUm_Y4LWKwJCqLs?key=WTdxUFREc01EZjNlV2FCbXFxOHZxUGJicFUxQWN3">Yuppie Psycho</a></br><a name = "ref_2_d"><a href = "#ref_2_d">[2]</a></a>&nbsp;<a href = "#ref_2_s">&nbsp;↑&nbsp;</a>&nbsp;<a href = "https://www.right.com.cn/forum/thread-199299-1-1.html">NAT原理</a></br><a name = "ref_3_d"><a href = "#ref_3_d">[3]</a></a>&nbsp;<a href = "#ref_3_s">&nbsp;↑&nbsp;</a>&nbsp;<a href = "https://github.com/HMBSbige/NatTypeTester">NAT类型检测工具</a></escape>

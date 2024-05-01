---
layout:     post
title:      资源使用注意事项
date:       2019-05-28 15:00:00
author:     "冰灵"
categories:
    - 资源
tags:
    - 网盘
    - torrent
    - magnet
thumbnail: "https://i.ytimg.com/vi/h48ilOz_eEs/maxresdefault.jpg"
---
>题图来源<escape><a name = "ref_1_s" href="#ref_1_d"><sup>[1]</sup></a></escape>
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。

<escape><font size=4>目录</font></escape>

1. [网盘](#网盘)
   - 1.1 [提取码位置](#提取码位置)
   - 1.2 [文件名](#文件名)
   - 1.3 [防限速](#防限速)
   - 1.4 [实用批处理分享](#实用批处理分享)
2. [磁链及种子](#磁链及种子)
3. [播放器](#播放器)
4. [注释](#注释)

### 网盘

字幕加载问题见[播放器](#播放器)一节。

#### 提取码位置

正文中链接文字旁圆括号内均为百度网盘提取码，链接不特别说明均为百度网盘分享链接。未标注提取码的百度网盘链接，提取码已附在链接中，不需要单独输入。

若有MEGA网盘分享链接，则提取码已包含在链接内。

#### 文件名

如果遇到没有后缀名的文件，其实都是7z格式，请使用能解压7z格式的压缩软件将其解压。

文件夹名为seed指种子，sub指字幕文件。

#### 防限速

百度网盘破解限速工具[pandownload][pandownload_site]使用建议

- 对默认设置进行调整，最大连接不超过5，并行任务不超过3，不然可能会被强制限速。

#### 实用批处理分享

- 批量重命名批处理：用来把资源里的各类文件按照给定的txt进行重命名。
- 批量压缩批处理：用来压缩出和分享出来的视频压缩版一样的，一集一个压缩包的批处理。

详见[冰灵windows批处理使用说明](冰灵win批处理.html)

### 磁链及种子

磁链和种子下载请使用指定软件，不建议用迅雷。迅雷可能因版权封禁下载，而且其吸血行为对bt社区有害。

windows

- [qbittorent][qbt_site]
- utorrent

android

- [utorrent][utorrent_site]

ios

- 对不起，app store不让这类应用上架

如果使用公网bt时，DHT结点为0，或者Tracker服务器无法工作，可能是你本地网络禁止bt下载导致的，建议切换网络运营商，或者使用网盘资源来解决问题。

如果DHT和Tracker服务器都能工作却没有速度，通常是由于网络上没人做种导致的，这种情况下你可以选择长时间挂种等待，或者使用网盘资源。

下载完成后，建议在自身条件允许的情况下进行做种，方便他人下载。使用网盘资源的，也可以将相关资源恢复至做种状态。

### 播放器

请使用能正常播放mkv格式的播放器

- 包括读取各式字幕文件和加载内封字体的功能
- **如果百度在线无法正常播放出内封字幕，请下载至本地，使用以下播放器播放**

windows

- MPC-HC
- VLC
- 弹弹Play(可播放xml格式弹幕文件)
- potplayer

android

- MX player

ios

- Infuse
- nPlayer

播放器进阶调整：[[VCB-Studio 科普教程 2.2] 基于 PotPlayer 和 madVR 的播放器教程（已更新 XySubFilter）][VCB_S_tutorial_videoplayer]

### 注释

点击上箭头字符可返回原位置，方括号中的数字表示引用的次序。
<escape></br><a name = "ref_1_d" href = "#ref_1_d">[1]</a></escape> <escape><a href = "#ref_1_s">↑</a></escape> <escape><a href = "https://youtu.be/h48ilOz_eEs">Yuppie Psycho - Welcome to Sintracorp thumbnail</a>

[pandownload_site]: http://pandownload.com
[qbt_site]: https://www.fosshub.com/qBittorrent.html
[utorrent_site]: https://www.utorrent.com/intl/zh/downloads/android
[VCB_S_tutorial_videoplayer]: https://vcb-s.com/archives/7228
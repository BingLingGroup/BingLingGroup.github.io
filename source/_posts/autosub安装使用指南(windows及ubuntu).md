---
layout:     post
title:      autosub安装使用指南(windows及ubuntu)(200302)
date:       2019-02-10 21:00:00
author:     "冰灵"
categories:
    - 演示
tags:
    - 教程
    - python
    - ubuntu
    - windows
    - autosub
    - 字幕
    - 自动字幕
thumbnail: "https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/autosub%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97(windows%E5%8F%8Aubuntu)/[Crappy%201080P]%20Code%20Lyoko%20S2E41_000859.164_0.png"
---
>[题图来源\(Code Lyoko E41的08分59秒位置\)][E410859]将浏览器拉窄即可看到全图。
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。
>**autosub-0.4.0及以上版本支持python3。本文部分内容已过时，且不会更新，新的安装使用指南详见[autosub/README.zh-Hans.md at dev · BingLingGroup/autosub](https://github.com/BingLingGroup/autosub/blob/dev/docs/README.zh-Hans.md)。**

<escape><font size=4>目录</font></escape>

1. [简介](#简介)
2. [windows python2.7环境安装配置](#windows-python2-7环境安装配置)
   - 2.1 [没安装过python](#没安装过python)
   - 2.2 [安装过python](#安装过python)
3. [ubuntu python2.7环境安装配置](#ubuntu-python2-7环境安装配置)
4. [安装pip](#安装pip)
   - 4.1 [pip安装的注意事项](#pip安装的注意事项)
5. [安装ffmpeg](#安装ffmpeg)
6. [windows使用pip安装autosub](#windows使用pip安装autosub)
7. [ubuntu使用pip安装autosub](#ubuntu使用pip安装autosub)
8. [使用autosub](#使用autosub)
9. [不能稳定连接google服务器的网络问题](#不能稳定连接google服务器的网络问题)
10. [google~~见人下菜~~的网络问题](#google见人下菜的网络问题)
11. [其他问题](#其他问题)
12. [自动翻译功能](#自动翻译功能)
13. [图形界面使用](#图形界面使用)
14. [字幕格式批量转换](#字幕格式批量转换)
15. [附录](#附录)
   - 15.1 [为什么此处不推荐使用windows？](#1-为什么此处不推荐使用windows？)
   - 15.2 [为什么此处推荐使用ubuntu？](#2-为什么此处推荐使用ubuntu？)
   - 15.3 [如何查看apt包管理器中的软件信息？](#3-如何查看apt包管理器中的软件信息？)
   - 15.4 [python3命令的切换方法](#4-python3命令的切换方法)
   - 15.5 [软件的默认输出处理逻辑问题](#5-软件的默认输出处理逻辑问题)
   - 15.6 [把google批判一番的无端联想](#6-把google批判一番的无端联想)
   - 15.7 [autosub windows使用问题疑难解答](#7-autosub-windows使用问题疑难解答)
   - 15.8 [autosub api调用及语音识别原理概览](#8-autosub-api调用及语音识别原理概览)

### 简介

[autosub的readme][autosub_readme]简介的[google翻译][google_translate_readme]

>Autosub是一种用于自动语音识别和字幕生成的实用程序。它将视频或音频文件作为输入，执行语音活动检测以查找语音区域，向google Web Speech API发出并行请求以生成这些区域的转录，（可选）将它们转换为其他语言，最后保存结果字幕到本地。它支持各种输入和输出语言（使用参数--list-languages运行程序可查看支持的语言），并且当前可以生成SRT格式或简单JSON的字幕。

由于使用了google的语音识别API，~~而且提供了免费使用的google语音识别API key~~，可以说autosub使用的是目前普通人可接触到的顶级的语音识别API也不为过。

### windows python2.7环境安装配置

[\[1\]为什么此处不推荐使用windows？](#1-为什么此处不推荐使用windows？)

#### 没安装过python

如果你的windows之前没有安装过python，直接到python官网上下载安装python2.7，注意安装时在customize python 2.7界面下划到最底下选择Add Python.exe to Path。

<escape><div title="Add Python.exe to Path" align="middle"><img src="https://cloud.githubusercontent.com/assets/20913258/17700048/c3d84166-6389-11e6-9cda-2144e2c98ade.png" height="50%" width="50%"></div></escape>
<escape><div align="middle">Add Python.exe to Path</div></escape>

也可以考虑使用windows第三方包管理器[chocolatey][choco_install_site]安装python2.7。

安装好chocolatey之后，用管理员权限运行命令行或者Powershell(譬如Win+X调出快捷键菜单运行)，输入以下指令来安装python2.7。

```bash
choco install python2 -y
```

[下一步：安装pip](#安装pip)

#### 安装过python

如果你的windows安装过python2.7且没安装过python3，那么可以忽略掉python2.7环境安装配置这一部分了。

如果你的windows安装过python3，且在种种原因之下不能卸载python3，那么你需要查看[windows python2与python3环境共存简易方法](windows python2与python3环境共存简易方法.html)。

[下一步：安装pip](#安装pip)

### ubuntu python2.7环境安装配置

[\[2\]为什么此处推荐使用ubuntu？](#2-为什么此处推荐使用ubuntu？)

ubuntu的python2.7一般是自带的，你可以通过

```bash
python -V
```

查看当前python版本(注意**V**是大写)，如果python没有安装，可以通过

```bash
apt install python -y
```

安装python2.7。[\[3\]如何查看apt包管理器中的软件信息？](#3-如何查看apt包管理器中的软件信息？)

如果已安装的python命令对应的是python3的版本，而python2.7已经安装，可以通过[update-alternatives][update_alternatives]这个命令来切换python版本。

相关参考[\[4\]python3命令的切换方法](#4-python3命令的切换方法)

ubuntu下一般python命令用于使用python2.7，python3命令用于使用python3

### 安装pip

通过[pip官方文档][pip_install_docs]安装最新版即可。windows用户可以通过浏览器打开第一条指令中的那个链接，然后Ctrl-S另存为get-pip.py文件，在get-pip.py所在的文件夹打开命令行或者powershell，运行第二条指令即可。

#### pip安装的注意事项

- 运行上述指令时使用的是对应着python2.7版本的python指令
- ubuntu用户也可以使用apt包管理器中的python-pip软件包进行安装
- windows用户不建议使用chocolatey中的pip进行安装，版本过旧
- 如果遇到了任何安装问题，一般通过[pip官方文档][pip_install_docs]的方法重新安装pip都可以解决

### 安装ffmpeg

windows建议使用[chocolatey][choco_install_site]安装ffmpeg。

```bash
choco install ffmpeg -y
```

ubuntu则使用apt

```bash
apt install ffmpeg -y
```

### windows使用pip安装autosub

由于原版autosub部分代码没有考虑到windows的问题，所以需要安装特别的版本。

大家可以使用我fork的已经修改过源代码的可以在windows上安装使用的autosub的版本[BingLingGroup/autosub][BingLing_forked_autosub]。

有两种安装方法，一种是点击刚才这个项目主页右侧Clone or download按钮，在弹出的菜单中选择Download ZIP。

<escape><div title="Clone or download" align="middle"><img src="https://help.github.com/assets/images/help/repository/clone-repo-clone-url-button.png" height="50%" width="50%"></div></escape>
<escape><div align="middle">Clone or download</div></escape>

<escape><br></escape>
<escape><br></escape>

<escape><div title="Download ZIP" align="middle"><img src="https://help.github.com/assets/images/help/repository/https-url-clone.png" height="50%" width="50%"></div></escape>
<escape><div align="middle">Download ZIP</div></escape>

然后解压该zip文件，切换到setup.py所在目录，然后运行这条命令。这句命令最后有一个"."表示当前目录。

```bash
pip install .
```

[下一步：使用autosub](#使用autosub)
<escape><br></escape>
<escape><br></escape>

另一种是安装git，你可以使用[choco][choco_install_site]来安装git

```bash
choco install git -y
```

然后使用下面这条指令进行安装，也就是[pip的VCS功能][pip_vcs]

```bash
pip install git+https://github.com/BingLingGroup/autosub.git@origin
```

如果你对我修改的代码产生疑虑，可以自己根据[Install AutoSub Step to Step in Windows with Translate subtitle #31][issue_31]进行安装，我所作的改动基本上就是这个问题里提到的那些。

也可以查看仓库对应的autosub-0.4.0-alpha版的[更新日志][Changelog]和[提交历史][commit_history]。

[下一步：使用autosub](#使用autosub)

### ubuntu使用pip安装autosub

ubuntu用户运行以下指令，从PyPI(Python Package Index也即Python软件包索引)中安装autosub 0.3.12版，虽然版本没有原作者仓库[agermanidis/autosub][agermanidis_autosub]里的新，但是不影响使用

```bash
pip install autosub
```

或者安装git

```bash
apt install git -y
```

然后再通过[pip的VCS功能][pip_vcs]安装github仓库里的代码

```bash
pip install git+https://github.com/agermanidis/autosub.git@master
```

### 使用autosub

在命令行界面输入autosub -h可以得知autosub的输入参数。由于目前软件未提供翻译api而只提供了语音识别api，所以在不提供-K选项的情况下，所有尝试翻译的参数输入，即-S和-D的参数不一致的情况下都会失败。

想了解自动翻译功能的可以跳转至[自动翻译功能](#自动翻译功能)。

除此之外软件还有逻辑bug，所以建议输全-S和-D参数，格式类似以下这种

```bash
autosub -S zh-CN -D zh-CN [你的视频/音频文件名]
```

新建记事本-复制粘贴该行命令-修改后缀名为.bat即可双击使用，需要观看错误输出时注意在末尾加上call cmd，或者在命令行中运行。

[\[5\]软件的默认输出处理逻辑问题](#5-软件的默认输出处理逻辑问题)

### 不能稳定连接google服务器的网络问题

首先最大的问题是网络问题，如果你使用的是无法连接到google服务器的网络，windows端你可能需要在命令行界面下输入以下两个指令，以改变当前命令行的http proxy。注意http proxy一般由本地软件提供，譬如[克莱士][kelaishi_win]，127.0.0.1指本地IP，冒号后面的是本地软件提供的http proxy端口。

```batch
set http_proxy=http://127.0.0.1:1080
set https_proxy=https://127.0.0.1:1080
```

ubuntu也需要类似的指令给终端上代理，只是你需要注意本地proxy软件是否提供http proxy功能，如果只提供socks5 proxy，你需要使用[polipo][csdn_polipo]将其转为http proxy然后使用。

然而你依然可能遇到如图所示的错误(Connection broken)，多是因为你的网络不够稳定导致的，原因大概是google speech api对网络比较挑剔。

<escape><div title="Clone or download" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/autosub%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97(windows%E5%8F%8Aubuntu)/autosub_network.png" height="80%" width="80%"></div></escape>
<escape><div align="middle">Clone or download</div></escape>

遇到这种错误，你可能需要更换网络环境。通常来讲，将运行平台更换为可稳定连接至google服务器的云服务器会比更换proxy更加有效，具体方式参考[\[2\]为什么此处推荐使用ubuntu？](#2-为什么此处推荐使用ubuntu？)

### google~~见人下菜~~的网络问题

简言之：

- 目前版本(0.4.0及以下版本)的autosub不要用香港IP，-S zh-CN的参数，去识别普通话的语音，不然会按照粤语识别输出繁体粤语(yue-Hant-HK)，识别结果也是完全错误。可以使用香港IP识别en，不会有影响。至于其他亚洲地区的IP，暂时没有尝试，不知道会不会对zh-CN识别普通话这一情况产生影响
- 问题的具体分析参见[\[8\]autosub api调用及语音识别原理概览](#8-autosub-api调用及语音识别原理概览)

### 其他问题

如果你还遇到了一些问题，请先google错误代码，也可以参考[\[7\]autosub windows使用问题疑难解答](#7-autosub-windows使用问题疑难解答)。

### 自动翻译功能

autosub并不自带免费google翻译API key，所以需要正常使用翻译功能，你可以考虑以下方法：

- 使用在google上搜索可以白嫖的google翻译API key，用-K选项输入给autosub进行自动翻译

- 其他提供了*免费* 翻译API key的修改版autosub(**免责声明**，本文作者未尝试其有效性)：

  - [iWangJiaxiang/autosub][iWangJiaxiang_autosub]

- 关于辅助类字幕自动翻译校对工具，可以考虑[issue 31教程][issue_31]Translate your Subtitles那部分提到的[Subtitle Edit][sub_edit]

- 将视频上传至youtube，使用youtube-dl获取自动翻译字幕

- 付费使用google翻译API key

[返回使用autosub](#使用autosub)

### 图形界面使用

嫌弃命令行界面的用户可以考虑一个GUI版本[pyTranscriber][pyTranscriber_github](**免责声明**，本文作者未尝试其有效性)

### 字幕格式批量转换

请使用ffmpeg对字幕格式进行转换，也可以考虑该[windows批处理脚本][ffmpeg_sub_batch]。和附录[\[2\]](#2-为什么此处推荐使用ubuntu？)所说的批处理使用方法类似，输入格式和输出格式均可修改，参考[HowToConvertSubtitleToASS – FFmpeg][HowToConvertSubtitleToASSFFmpeg]，[ExtractSubtitles – FFmpeg][ExtractSubtitlesFFmpeg]。关于.sub等图形格式字幕的转换，建议使用[Subtitle Edit][sub_edit]，校对起来更方便。

### 附录

#### \[1\]为什么此处不推荐使用windows？

<escape><div title="用错图了.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/autosub安装使用指南(windows及ubuntu)/sticker_yczaebag.png" height="40%" width="40%"></div></escape>
<escape><div align="middle">ArchLinux使人笑颜倍增</div></escape>

*不推荐在windows下安装使用autosub*，除非

- *首先，你有着可**稳定**连接google服务器的网络环境*
- *其次，**你自认为**windows比ubuntu更方便使用，哪怕有的ubuntu甚至不需要额外安装python环境*
- *再次，你需要容忍一些autosub代码中windows有问题而ubuntu没问题的部分，或者使用非原github仓库或者非PyPI上的autosub代码来解决问题*

[返回windows python2.7环境安装配置](#windows-python2-7环境安装配置)

#### \[2\]为什么此处推荐使用ubuntu？

- *如果你肉身能**稳定**连接google服务器，依然建议使用ubuntu操作，因为更容易安装使用python和autosub*
  - *同时请忽略以下这段说明*

- *此处推荐的ubuntu环境一般为可**稳定**连接google服务器的ubuntu服务器*
  - *例如安装了ubuntu的虚拟专用服务器(**V**irtual **P**rivate **S**erver)或者弹性计算服务器(Elastic Compute Service)或者独立服务器(Dedicated Server)*
  - *远程服务器一般不可安装windows，即使可选，ubuntu的服务器软件环境还是比windows高到不知道哪里去了*
  - *其他linux系统的使用此处略去*
  
远程服务器操作指引：

- 远程服务器ssh连接工具[cmder][phpgao_cmder](ssh连接命令[*如何登陆我的vps*][phpgao_ssh])，xshell，MobaXterm等等
- 远程文件交互工具winscp(文件上传下载)，[caddy][imnerd_caddy](文件下载)，jQuery-File-Upload(文件上传)
- ubuntu ssh配置，ubuntu ssh服务启动等等
- 建议上传时只上传音频文件，上传视频文件既耗时也占用服务器存储空间
- 以下是windows调用ffmpeg批量抽取当前文件夹下的视频的音频的批处理，新建记事本-复制粘贴代码-修改后缀名为.bat即可使用。由于autosub使用ffmpeg进音频转码，且无论什么音频或视频格式输入，都会转换为flac格式，所以此处音频输出采用非编码输出mka万能封装效率最高

```batch
@echo off
set "in_format=*.webm *.mp4"
rem 根据需要这里in_format修改为自己要输入的格式
rem 注意不要去掉通配符*号
rem 暂时不支持批量抽取一个视频中的多个音轨
set "out_format=.mka"
rem 此处输出格式不要修改，否则可能会输出失败
rem 因为当前为非编码模式，只能使用mka这种万能封装

@echo on
for /f "delims=^" %%i in ('dir /b %in_format%') do (
    ffmpeg -i "%%i" -vn -acodec copy "%%~ni%out_format%"
)
@echo off
rem 此处会将当前文件夹下的所有视频的音频进行抽取
rem 文件名和原来的一致，扩展名为你设置的输出格式

call cmd
```

- 如果安装了git bash或者其他可在windows下运行bash语言的终端，可以使用这个对格式有判断的bash脚本[bash - how can I batch extract audiofrom mp4 files with ffmpeg without decompression (automatic audio codec detection)? - Ask Ubuntu][askubuntu_bash_ffmpeg_audio]
- ubuntu端批量识别音频的bash脚本${C\infty ming}$ ${S\infty n}^{TM}$

以及一些估计没人会和我一样踩的坑：

- 如果你使用的ubuntu服务器内存空闲空间小于150MB，可能会遇到内存不够用的问题，错误信息会显示内存空间不够，分配失败，请关闭部分后台程序后再运行autosub即可。内存占用主要是调用ffmpeg转码音频为flac格式时发生的。
- 虽然语音识别的任务是由google服务器进行，而音频分析时间轴生成的任务是在本地完成的，可以说识别速度的瓶颈基本不在本地，但是对于少数CPU特别弱的ubuntu服务器(点名批评半碗果20刀祖传OVZ架构单核服务器)，可能会遇到音频分析时间对CPU占用过大拖累识别速度的问题。我这里并不是建议你非得用多核服务器，我是说最好别碰OVZ架构。

[返回ubuntu python2.7环境安装配置](#ubuntu-python2-7环境安装配置)

#### \[3\]如何查看apt包管理器中的软件信息？

Ubuntu apt包管理器中的python软件包目前版本依然是python2.7，可以通过

```bash
apt-cache show package python
```

查看python包的详情。

[返回ubuntu python2.7环境安装配置](#ubuntu-python2-7环境安装配置)

#### \[4\]python3命令的切换方法

```bash
update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.x 1
update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.y 2
update-alternatives --config python3
```

x和y代表某个python3的版本，以上方法来源[搞定了最新版本 EFB2.0.0， telegram 收发微信，工作正常。 - V2EX][v2ex_efb2]。

[返回ubuntu python2.7环境安装配置](#ubuntu-python2-7环境安装配置)

#### \[5\]软件的默认输出处理逻辑问题

<escape><div title="Error: Subtitle translation requires specified google Translate API key." align="middle"><img src="https://user-images.githubusercontent.com/8603085/38403193-cb5a5e04-398b-11e8-8472-3dd3a73455f7.png" height="100%" width="100%"></div></escape>
<escape><div align="middle">该逻辑问题的错误信息输出</div></escape>

```bash
C:\>autosub -h
usage: autosub [-h] [-C CONCURRENCY] [-o OUTPUT] [-F FORMAT] [-S SRC_LANGUAGE]
               [-D DST_LANGUAGE] [-K API_KEY] [--list-formats]
               [--list-languages]
               [source_path]

positional arguments:
  source_path           Path to the video or audio file to subtitle

optional arguments:
  -h, --help            show this help message and exit
  -C CONCURRENCY, --concurrency CONCURRENCY
                        Number of concurrent API requests to make
  -o OUTPUT, --output OUTPUT
                        Output path for subtitles (by default, subtitles are
                        saved in the same directory and name as the source
                        path)
  -F FORMAT, --format FORMAT
                        Destination subtitle format
  -S SRC_LANGUAGE, --src-language SRC_LANGUAGE
                        Language spoken in source file
  -D DST_LANGUAGE, --dst-language DST_LANGUAGE
                        Desired language for the subtitles
  -K API_KEY, --api-key API_KEY
                        The google Translate API key to be used. (Required for
                        subtitle translation)
  --list-formats        List all available subtitle formats
  --list-languages      List all available source/destination languages
```

根据87号拉取请求[Perform speech recognition if dst_language is not denied. #87][autosub_pr_87]，在视频源语言(SRC_LANGUAGE)不是默认字幕文件目标语言(DEFAULT_DST_LANGUAGE)en时，软件逻辑会出现问题，认为你希望将语音识别请求由视频源语言翻译成默认字幕文件目标语言。

根据python的参数语法分析逻辑，如果你不给定某一参数的值，譬如-D参数的值，程序会使用默认值，默认值这里原作者使用的是给定的en，而不会根据-S的值变化，所以有悖一般用户的使用逻辑。

[返回使用autosub](#使用autosub)

#### \[6\]把google批判一番的无端联想

破案了，参考附录[\[8\]](#8-autosub-api调用及语音识别原理概览)，以下内容已过期。

这个问题就很玄学了，我尝试过en和zh-CN的语音识别，但是只在zh-CN的语音识别上遇到过。查看--list-languages参数可知，zh-CN指的是Chinese (Simplified)，zh-TW指的是Chinese (Traditional)，但是你如果使用香港的IP地址使用zh-CN的参数对语音进行识别，会识别出繁体粤语来，~~这既不简体也不普通话啊，难道google想暗示在香港地区zh-CN里的CN指的其实是Cantonese？《震惊！404公司又一乳滑石锤》~~，关键是autosub不给你一个香港地区识别**普通话简体中文**的参数(其实也不完全，看后文)，而且如果你拿普通话的音频当作粤语去识别，那结果肯定是没法对上号的。

~~而且实话讲只是支持粤语，又不是支持更加政治正确的吴语([没有吴语][Cloud_Speech_to_Text_API])，显然也无法给google，用支持少数语言的名义洗地，这只是纯粹的商业化行为而已~~

~~暂时没试在香港地区使用zh-TW参数能否按照普通话Mandarin识别出繁体，这样至少我还能把文本复制到word里面繁体转简体，说明我对常凯申的疯狂转进流学习得还不够透彻~~

但是如果是使用美国的IP，那么zh-CN的识别结果就是很正常的，~~google怎么会觉得法拉盛的高华用的是简体中文~~。我之前看过代码，autosub没有对语言代码做过手脚，都是直接传给api了，~~那只能说是google爸爸又**不作恶**了~~，今且按不下表。

那么对于我们这些不能左右~~根据你IP个性化推荐语音识别结果~~这些大公司的普通~~白嫖~~用户来讲，只能从根子上入手，用美国IP就是了。~~生是洛圣都的人，死是洛圣都的鬼。~~

~~再补充一下，我看了一下google speech api的文档，对于language code这一点而言已经有了新的标准[语言支持 | Cloud Speech-to-Text API][Cloud_Speech_to_Text_API]。但是仍然很难解释，凭什么我给zh-CN的参数，google用我的IP，就给我转换成yue-Hant-HK了，要么你不给我转换报错也可以啊。不过我看了一下新版的api和autosub里面[constants.py][autosub_constant_py]的区别，确实也有pull request的余地，等以后作进一步研究吧。~~

(当然我也没试验过除了香港以外亚洲地区zh-CN的识别结果如何，没钱啊)

#### \[7\]autosub windows使用问题疑难解答

[Exception: Dependency not found: ffmpeg · Issue #94 · agermanidis/autosub](https://github.com/agermanidis/autosub/issues/94)

[Temp Folder Permissions Denied on Windows 10 · Issue #15 · agermanidis/autosub](https://github.com/agermanidis/autosub/issues/15)

[返回其他问题](#其他问题)

#### \[8\]autosub api调用及语音识别原理概览

为了研究language code在autosub里面的使用情况，我开始查看autosub的源代码，研究了半天它这api的调用方法，也翻了一会issue区的问题，才发现我前面完全搞错了这个api的来源。首先根据issue区里面的[your api key #1][issue_1]开发者的回答，他这个api就是从chromium的源代码上面扒下来的，我发现这个api和cloud speech api其实没有太大关系，自然用法也不一样。具体情况可以参考这个回复[api key Is it a charge item? #111][issue_111]。我在google上搜到这么一个项目[google-speech-v2][google_speech_v2]，对这个api的使用提供了一点参考。我接下来有空会对修改后的代码进行测试，如果这个api能识别cloud speech api里面的语言代码，我会提交pull request对主项目进行改进。

[返回google~~见人下菜~~的网络问题](#google见人下菜的网络问题)

[E410859]: https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/autosub%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97(windows%E5%8F%8Aubuntu)/[Crappy%201080P]%20Code%20Lyoko%20S2E41_000859.164_0.png
[autosub_readme]: https://github.com/agermanidis/autosub/blob/master/README.md
[google_translate_readme]: https://translate.google.com/#view=home&op=translate&sl=en&tl=zh-CN&text=Autosub%20is%20a%20utility%20for%20automatic%20speech%20recognition%20and%20subtitle%20generation.%20It%20takes%20a%20video%20or%20an%20audio%20file%20as%20input%2C%20performs%20voice%20activity%20detection%20to%20find%20speech%20regions%2C%20makes%20parallel%20requests%20to%20google%20Web%20Speech%20API%20to%20generate%20transcriptions%20for%20those%20regions%2C%20(optionally)%20translates%20them%20to%20a%20different%20language%2C%20and%20finally%20saves%20the%20resulting%20subtitles%20to%20disk.%20It%20supports%20a%20variety%20of%20input%20and%20output%20languages%20(to%20see%20which%2C%20run%20the%20utility%20with%20the%20argument%20--list-languages)%20and%20can%20currently%20produce%20subtitles%20in%20either%20the%20SRT%20format%20or%20simple%20JSON.
[choco_install_site]: https://chocolatey.org/docs/installation
[update_alternatives]: https://blog.csdn.net/u013894834/article/details/75305752
[pip_install_docs]: https://pip.pypa.io/en/stable/installing/
[BingLing_forked_autosub]: https://github.com/BingLingGroup/autosub
[pip_vcs]: https://pip.pypa.io/en/stable/reference/pip_install/#vcs-support
[Changelog]: https://github.com/BingLingGroup/autosub/blob/alpha/docs/CHANGELOG.zh-Hans.md#040-alpha---2019-02-17
[commit_history]: https://github.com/BingLingGroup/autosub/commits/origin
[issue_31]: https://github.com/agermanidis/autosub/issues/31
[sub_edit]: https://github.com/SubtitleEdit/subtitleedit/releases
[agermanidis_autosub]: https://github.com/agermanidis/autosub
[kelaishi_win]: https://github.com/Fndroid/clash_for_windows_pkg
[csdn_polipo]: https://blog.csdn.net/Jesse_Mx/article/details/52863204
[iWangJiaxiang_autosub]: https://github.com/iWangJiaxiang/autosub/tree/master
[Cloud_Speech_to_Text_API]: https://cloud.google.com/speech-to-text/docs/languages
[autosub_constant_py]: https://github.com/agermanidis/autosub/blob/master/autosub/constants.py
[pyTranscriber_github]: https://github.com/raryelcostasouza/pyTranscriber
[ffmpeg_sub_batch]: https://github.com/Bourshevik0/subtitle_works/blob/master/youtube-dl%20batch/ffmpeg_vtt2srt.bat
[HowToConvertSubtitleToASSFFmpeg]: https://trac.ffmpeg.org/wiki/HowToConvertSubtitleToASS
[ExtractSubtitlesFFmpeg]: https://trac.ffmpeg.org/wiki/ExtractSubtitles
[phpgao_cmder]: https://blog.phpgao.com/cmder.html
[phpgao_ssh]: https://blog.phpgao.com/post_buy_faq.html
[imnerd_caddy]: https://imnerd.org/use-caddy-replace-nginx.html
[askubuntu_bash_ffmpeg_audio]: https://askubuntu.com/questions/221026/how-can-i-batch-extract-audio-from-mp4-files-with-ffmpeg-without-decompression
[v2ex_efb2]: https://www.v2ex.com/t/429372#r_5389764
[autosub_pr_87]: https://github.com/agermanidis/autosub/pull/87
[issue_1]: https://github.com/agermanidis/autosub/issues/1
[issue_111]: https://github.com/agermanidis/autosub/issues/111#issuecomment-463046630
[google_speech_v2]: (https://github.com/gillesdemey/google-speech-v2)

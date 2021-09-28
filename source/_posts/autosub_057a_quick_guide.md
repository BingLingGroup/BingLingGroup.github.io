---
layout:     post
title:      autosub-0.5.7a安装使用极速指南
date:       2020-05-07 21:00:00
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
thumbnail: "https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/autosub_057a_quick_guide/[Crappy%201080P]%20Code%20Lyoko%20S4E91.mp4_002317.431.jpg"
---
>[题图来源\(Code Lyoko E91的23分17秒位置\)](https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/autosub_guide/[Crappy%201080P]%20Code%20Lyoko%20S4E91.mp4_002317.431.jpg)将浏览器拉窄即可看到全图。
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。
>**请配合readme使用[autosub/README.zh-Hans.md at dev · BingLingGroup/autosub](https://github.com/BingLingGroup/autosub/blob/dev/docs/README.zh-Hans.md)。**

<escape><font size=4>目录</font></escape>

1. [简介](#简介)
2. [下载](#下载)
3. [Google Speech V2使用方法](#google-speech-v2使用方法)
4. [讯飞云流式WebAPI](#讯飞云流式webapi)
5. [翻译字幕](#翻译字幕)
6. [尾声](#尾声)

### 简介

简单提下，autosub是一个字幕自动生成工具。它能使用auditok来自动检测语音区域，通过ffmpeg根据语音区域来切割音频，通过多个API将语音转为文字，以及通过py-googletrans将字幕文本翻译。

目前只支持短语音识别，也就是API不返回句子时间戳，需要本地进行分句和分割音频的那种。目前支持的API为Google Speech V2，Google Cloud Speech-to-Text，讯飞开放平台语音听写流式版WebAPI，百度短语音识别/短语音识别极速版。本期将主要讲解Google Speech V2，讯飞，py-googletrans的使用方法。

请注意，目前本程序自身不提供任何语音识别和翻译的功能，所有语音识别和翻译的功能都来自于公开的API，具体来讲，不仅需要在使用时保持联网，也需要用户在特定情况下自己注册相关账号，其所产生的费用与本程序无关，且本程序许可GPLv2中已有相关声明，本程序不对其行为作任何担保。如果需要任何帮助，欢迎通过各种联系方式有偿咨询我。

### 下载

这里主要讲解windows用户如何下载使用独立发布包，关于使用python环境和pip进行安装的方法请参考另一期的说明。

点开项目主页——当然如果你打不开github，那么请用微云的版本——点击中间的release，找到最上面这个0.5.7-alpha发布的Assets，点击这个三角形展开，选择其中一个下载，我个人推荐用nuitka，因为启动速度比较快，体积也比较小。

下载完以后解压，现在autosub支持双击启动，只是你双击之后仍然是需要输入参数。

### Google Speech V2使用方法

如果你需要识别中文，可以跳过这一节，因为谷歌的中文语音识别真的很一般。

这个API的密钥是公开的，使用它不需要注册账户，也不会产生费用，但是请不要滥用它。

如果你能直连谷歌，使用以下指令：

```bash
autosub -i 输入视频或音频文件 -S 语言代码
```

语言代码需要用`-lsc`进行查看，譬如美式英语使用`en-US`。

然后回车运行即可。

如果你不能直连谷歌，需要使用http proxy，请在以上输入选项的基础上加上这个选项:

```bash
-hsp
```

只输入`-hsp`意味着使用了const参数，或者说是将环境变量http_proxy改成了`https://127.0.0.1:1080`，如果你需要修改端口或者地址，请把你需要输入的参数填写在这个选项后面，如:

```bash
-hsp http://127.0.0.1:12345
```

### 讯飞云流式WebAPI

这个API需要自己注册账户，超出免费额度后可能产生费用，一切后果自行承担。

使用以下指令：

```bash
autosub -sapi xfyun -i 输入视频或音频文件 -sconf 讯飞云语音配置文件
```

语音配置文件是json格式的，推荐使用[Visual Studio Code](https://code.visualstudio.com)这个文本编辑器进行编辑。这里简要说明一下，下载安装VScode以后，到扩展商店里安装JSON Tools插件，安装完了以后，使用`Ctrl + Alt + M`快捷键可以格式化JSON文件。

识别中文语言的json文件内容主要为下：

```json
{
    "app_id": "",
    "api_secret": "",
    "api_key": "",
    "business": {
        "language": "zh_cn",
        "domain": "iat",
        "accent": "mandarin"
    }
}
```

其中，app_id，api_secret，api_key是你在讯飞云控制台创建的新应用里，`语音听写（流式版）`中能找到的服务接口认证信息里的项目，请一一对应填写好即可。

### 翻译字幕

这个API的运行依赖于一个开源库py-googletrans，使用它不需要注册账户，也不会产生费用，但是请不要滥用它。

使用以下指令：

```bash
autosub -i 输入字幕文件 -SRC 源语言代码 -D 目的语言代码
```

语言代码需要用`-ltc`进行查看，譬如英语使用`en`，这与`-lsc`不同。

从识别出的字幕中翻译字幕，将以下选项加入前面所说的语音识别的命令中就可以了：

```bash
-SRC 源语言代码 -D 目的语言代码
```

也可以不输入选项`-SRC`，不输入时，程序自动判断输入语言的类型，类似谷歌翻译中的`自动识别源语言`的功能。

如果你无法连接`translate.google.com`，请在以上选项的基础上，添加该选项：

```bash
-surl "translate.google.cn"
```

这样就可以直接使用了。

### 尾声

因为是极简教程，篇幅有限，很多东西没有展开讲。更多信息请参考readme，help信息，或者后续的教程。当然啦，后续我也会出视频讲讲更多关于autosub的东西，不一定是教程，比如未来可能推出的功能。如果你觉得这期视频不错，或者想要支持autosub的开发，请通过以下方式支持我，我们下期再见。

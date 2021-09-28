---
layout:     post
title:      windows python2与python3环境共存简易方法
date:       2019-02-09 19:00:00
author:     "冰灵"
categories:
    - 演示
tags:
    - 教程
    - python
    - python2
    - python3
    - 环境变量
    - windows
thumbnail: "https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/windows%20python2%E4%B8%8Epython3%E7%8E%AF%E5%A2%83%E5%85%B1%E5%AD%98%E7%AE%80%E6%98%93%E6%96%B9%E6%B3%95/[Crappy%201080P]%20Code%20Lyoko%20S4E81_001355.582.png"
---
>[题图来源\(Code Lyoko E81的13分55秒位置\)][E811355]将浏览器拉窄即可看到全图。
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。

<escape><font size=4>目录</font></escape>

1. [简介](#简介)
2. [原理](#原理)
3. [安装](#安装)
4. [手动设置系统环境变量](#手动设置系统环境变量)
   - 4.1 [通过系统属性设置](#通过系统属性设置)
     - 4.1.1 [新建PY_HOME系统变量](#新建PY-HOME系统变量)
     - 4.1.2 [已经有Path这个变量](#已经有Path这个变量)
     - 4.1.3 [还没有Path这个变量](#还没有Path这个变量)
   - 4.2 [通过注册表进行设置](#通过注册表进行设置)
   - 4.3 [通过命令行setx命令和reg命令进行设置](#通过命令行setx命令和reg命令进行设置)
5. [自动设置系统环境变量](#自动设置系统环境变量)
6. [通过PY_HOME系统变量切换python版本](#通过PY-HOME系统变量切换python版本)
   - 6.1 [手动切换python版本](#手动切换python版本)
   - 6.2 [自动切换python版本](#自动切换python版本)
7. [本方法参考](#本方法参考)

### 简介

该简易方法可以做到在windows下“同时”安装python2和python3环境依赖且使用互不兼容的python软件包(如vapoursynth和autosub)，不会涉及到Pycharm python开发环境设置，[anaconda][anaconda_zhihu]的配置设置等等。

此处所指的vapoursynth与autosub的冲突是指，vapoursynth必须要使用python3以上的python运行环境，autosub必须要使用python2的python运行环境，而python3环境会影响到autosub的使用。autosub的[issue区的教程][autosub_issue_31]给出的解决方法竟然是卸载python3，我只能说我卸不起卸不起，太暴力了.jpg

### 原理

[环境变量 - 维基百科][wikipedia_env]
[Using Python on Windows - Python 3.7.2 documentation][py_win_install_docs]
简言之就是通过设置环境变量特别是系统环境变量Path，可以让python及python相关的软件包在命令行的非python环境目录下正常运行。

### 安装

首先是安装Python27和Python37，你可以使用[chocolatey][choco_install_site]安装python。

安装好chocolatey之后，用管理员权限运行命令行或者Powershell(譬如Win+X调出快捷键菜单运行)，输入以下指令来安装python27和python37。

```bash
choco install python2 -y
choco install python -y
```

如果你使用的是python的安装包进行的安装，可以考虑在安装过程中选择自定义功能并勾选Add python.exe to Path，使用choco安装时将自动设置环境变量。

安装时注意尽量使用默认安装路径，否则在后文提到的安装路径处请修改为自己的安装路径。

### 手动设置系统环境变量

但是python环境共存并不仅仅只是安装完两个版本的python这么简单，想要正常使用，你可以借助官方提供的[Python launcher for Windows][Py_launcher_win]以及具体使用方法[同时装了Python3和Python2，怎么用pip？ - 知乎][Py_launcher_zhihu]。

当然本篇文章所讲的并不是换个命令继续用的方法，~~因为是我实践完了以后才发现的这个方法，不想再试了~~，而是不需要改变原来的命令就可以直接用的方法。

>能用命令行做的事就不要用图形界面做

这话反过来就是：

>图形界面能做的事就不要用命令行做

以下将提到两种用GUI设置，两种用命令行设置系统环境变量的方法。

#### 通过系统属性设置

此电脑(我的电脑)-右键-属性-高级-环境变量，在弹出的窗口中可以看到上半部分用户变量和下半部分系统变量，根据这篇教程[Python环境变量][py_env_intro]，如果你看到用户环境变量或者系统环境变量里面有**PYTHONHOME**这个变量，务必删掉，否则会影响我后面提到的切换的方法。(**注意是变量，不是值，窗口里面有两列，第一列标的是变量，第二列是值**)同时删除和python有关的用户变量或者系统变量。

因为python命令输入时，程序一旦读到**PYTHONHOME**这个变量，就会去找这个目录下的python，而忽略掉其他变量的设置。

##### 新建PY_HOME系统变量

接下来点击新建(注意是系统变量的对话框，也就是下半部分对话框旁边的新建)，在弹出的窗口中的变量名框内输入**PY_HOME**，变量值输入你马上要用的Python.exe所在的路径，点确定来保存。

然后找到系统变量界面中的Path这个变量。

##### 已经有Path这个变量

选中Path变量，点击编辑，注意先删除已经存在的python的路径(如C:\Python27，C:\Python27\Scripts等)。

然后在弹出的窗口右侧点击新建，输入

```batch
%PY_HOME%
```

输完之后回车，再次重复以上步骤输入

```batch
%PY_HOME%\Scripts
```

然后点确定来保存。

如果觉得麻烦，也可以选择右侧的编辑文本，在最右侧或者最左侧添加，每一项之间用 **;** 分隔。

[下一步：通过PY-HOME系统变量切换python版本](#通过PY-HOME系统变量切换python版本)

##### 还没有Path这个变量

点击新建(注意是系统变量，也就是下半部分对话框旁边的新建)，在弹出的窗口中的变量名框内输入**Path**，变量值输入：

```batch
%PY_HOME%;%PY_HOME%\Scripts;
```

然后点确定来保存。

[下一步：通过PY-HOME系统变量切换python版本](#通过PY-HOME系统变量切换python版本)

#### 通过注册表进行设置

通过Win+R键调出运行，输入regedit打开注册表编辑器，在上方路径框中输入

>HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment

回车跳转至该位置，然后双击Path进行修改，以及在空白处右键新建字符串值**PY_HOME**，并输入数值数据，数据格式和前文所说方法类似。

[下一步：通过PY-HOME系统变量切换python版本](#通过PY-HOME系统变量切换python版本)

#### 通过命令行setx命令和reg命令进行设置

可以通过

```batch
setx /?
reg /?
```

查看使用方法，也可以谷歌其他教程，此处略过。

### 自动设置系统环境变量

我也写了一个使用reg和setx命令自动设置python系统环境变量的脚本win_py_syspath_sw_create.bat。

**[注意]**，本脚本会做出以下行为：

1. 申请管理员权限
2. 修改系统变量Path并创建系统变量PY_HOME
3. 在Path之前，将查询到的Path变量备份到txt文件内
4. 在Path之前，会自动删除Path中特定的六个路径，**可能和你之前设置的不一样**

免责声明：

1. 本人不对该脚本运行造成的任何后果负责，也不提倡任何人学习使用batch语言
2. 真正的懒人应该参考前面所说的手动设置方法进行设置

代码和下载详见[冰灵win批处理](冰灵win批处理.html#python环境批处理)。

### 通过PY_HOME系统变量切换python版本

日常使用时修改系统变量PY_HOME的值即可达到切换python环境的目的，注意修改后要记得重启命令行界面或者系统变量界面来载入系统变量的新值。

如果pip的使用出现异常情况，请通过[getpip的方法][pip_install]重装pip。

#### 手动切换python版本

类似地，[通过系统属性设置](#通过系统属性设置)和[通过注册表进行设置](#通过注册表进行设置)都可以修改PY_HOME的值。

#### 自动切换python版本

我也写了一个使用reg和setx命令自动切换PY_HOME系统环境变量的脚本win_py_syspath_sw.bat。

**[注意]**，本脚本会做出以下行为：

1. 申请管理员权限
2. 查询系统变量PY_HOME
3. 根据当前的python版本(只看PY_HOME的后两位数字)切换到另一个，**可能和你之前安装的路径名不一样**
4. 两者的默认取值为pyhome_1=27和pyhome_2=37，你可以根据自己的情况进行修改

免责声明：

1. 本人不对该脚本运行造成的任何后果负责，也不提倡任何人学习使用batch语言
2. 真正的懒人应该参考前面所说的手动设置方法进行设置

代码和下载详见[冰灵win批处理](冰灵win批处理.html#python环境批处理)。

### 本方法参考

本方法参考自[python - How to add to the pythonpath in Windows? - Stack Overflow][sof_pythonpath]。

其他类似的教程[Python多版本共存配置_哔哩哔哩 (゜-゜)つロ 干杯~-bilibili][python_multi_bili]。

[E811355]: https://ws1.sinaimg.cn/large/b07fd0f8ly1g00hpgpvxpj21hc0u07wh.jpg
[anaconda_zhihu]: https://zhuanlan.zhihu.com/p/22678445
[autosub_issue_31]: https://github.com/agermanidis/autosub/issues/31
[wikipedia_env]: https://zh.wikipedia.org/wiki/%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F
[py_win_install_docs]: https://docs.python.org/3/using/windows.html
[choco_install_site]: https://chocolatey.org/docs/installation
[Py_launcher_win]: https://www.python.org/dev/peps/pep-0397/
[Py_launcher_zhihu]: https://www.zhihu.com/question/21653286
[py_env_intro]: http://chenjiee815.github.io/pythonhuan-jing-bian-liang.html
[pip_install]: https://pip.pypa.io/en/stable/installing/#installing-with-get-pip-py
[sof_pythonpath]: https://stackoverflow.com/questions/3701646/how-to-add-to-the-pythonpath-in-windows/21433154#21433154
[python_multi_bili]: https://www.bilibili.com/video/av41868809
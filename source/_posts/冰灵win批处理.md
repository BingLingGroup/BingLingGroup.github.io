---
layout:     post
title:      冰灵win批处理(190209)
date:       2019-01-05 18:00:00
author:     "冰灵"
categories:
    - 工具
tags:
    - 冰灵制作组
    - windows
    - 批处理
    - batch
    - 批量重命名
    - 批量压缩
    - 7z
thumbnail: "https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/%E5%86%B0%E7%81%B5win%E6%89%B9%E5%A4%84%E7%90%86/[Crappy%201080P]%20Code%20Lyoko%20S4E80_001148.878.png"
---
>[题图来源\(Code Lyoko E80的11分48秒位置\)][E801148]将浏览器拉窄即可看到全图。
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>标题后面括号里的日期指的是最后更新日期，头像旁边的日期是最初发布日期。

<escape><font size=4>目录</font></escape>

1. [简介](#简介)
2. [批量重命名批处理](#批量重命名批处理-rename-files-from-txt)
   - 2.1 [为什么要写这样一个批处理](#为什么要写这样一个批处理)
   - 2.2 [功能](#功能)
   - 2.3 [使用](#使用)
3. [批量压缩批处理](#批量压缩批处理-7z-batch和run-7z-batch)
4. [python环境批处理](#python环境批处理)
5. [其他批处理](#其他批处理)

### 简介

这次来讲讲最近为了发布资源而写的几个windows batch批处理的使用指南。注意只能在windows上使用，~~谁叫batch是windows专用的脚本语言，只能被windows命令行解释器执行，但是写起来一点也不省心啊~~，以后大概会出同功能的python版，这样就可以跨平台运行了。

冰灵批处理相关的[github仓库][bingling_batch_github]，可以通过下载[仓库压缩文档][download_batch_zip]获得可以直接在windows上运行的.bat文件。目前项目readme还在施工中，~~因为我懒~~。

特别要注意的一点是，和其他命令行软件的输入一样，如果你的路径或者文件名里面有空格，那么请务必在外面加上引号。

### 批量重命名批处理(rename_files_from_txt)

#### 为什么要写这样一个批处理

其实很多软件都有批量重命名的功能，我平时用的[nexus file][nexus_file_homepage]在这方面功能就极其强大，譬如可以控制插入字符的位置，查找替换等等，那我为什么还要写这样一个批处理呢？

实际上，这些重命名软件，我现在还没看到哪个是支持全自定义列表重命名的，也就是，每一个文件名的内容都不一样，那有人问了，你既然每一个文件名内容都不一样，为什么不能一个个重命名非要写一个程序呢？其实这里是有一个相对合理的应用场景的。

1. 一个个重命名，就不说鼠标要一个个点浪费~~微动~~寿命了，F2键也会被摁坏，甚至不知道快捷键的人可能会摁坏第二个鼠标按键\(冷笑话\)。
2. 考虑一下是别人给你的文件名列表呢？那你可能还要多坏另外三个键盘的按键是Ctrl，C和V了\(滑稽\)

我就说说冰灵的应用场景。

1. 字幕组组长给你拟定了一个分集标题，每集标题都不一样。
2. 你是负责把视频上传到b站的，b站的分P名和很多网站处理上传文件的逻辑是一样的，默认值是上传前的文件名。\(a站就不是 ~~所以a站就不填分P名了~~\)
3. b站的分P名编辑起来比较鬼畜，好像是不能用鼠标点光标位置，修改起来困难。
4. 你会很自然想到先在本地就把文件名重命名好然后再上传。

譬如这样一个列表，一行一个名称

>S4E66_William Returns_William回归
>S4E67_Double Take_替身袭击
>S4E68_Opening Act_开幕演出
>S4E69_Wreck Room_毁坏房间
>......

那也就会很自然地想到写一个程序一行行读进来然后拿去重命名。

至于为什么用的批处理，~~主要是看到一个[b站压制大佬][bili_space]写的用来转换帧率的批处理不够懒人化而感到不满于是开始入坑~~，一开始是想着写着简单，后来发现越简单的东西越难写，特别是batch的中文文档不是很多~~很难抄代码~~的情况下，还好后来多看[官方文档][windows_batch_docs]和stackoverflow解决了一部分问题。

#### 功能

目前能做到的功能就是从一个源文件名txt和一个目的文件名txt中读取文件名，然后改名。其中源文件名txt支持自动生成，但是因为batch默认的文件名排序比较迷，和资源管理器中的文件名顺序并不一致。

最明显的一点是，按文件名顺序排序后，资源管理器里面1后面的2到9的数字会在10之前，而batch的文件名顺序是，2到9的数字会在10之后，只有你命名成等宽的数字编码，譬如最大不超过999则是001或者最大不超过99则是01这种，才会得到正确的排序。

所以本批处理会强制停下让你重新检查源文件名列表和目的文件名列表的一一对应关系，如果有问题建议复制到[excel][libre_office_homepage]中进行编辑，只要在这个步骤时，确认每一行对应关系没问题，那么最后重命名的结果就是正确的，毕竟程序核心只是遍历每一行txt，然后调用系统自带的重命名命令ren进行重命名而已。~~毕竟batch太过简略，拿来写排序算法也实在太难受所以后续估计不会在这方面进行改进了~~。

>什么？你电脑上还没有装excel？[libre office][libre_office_homepage]了解一下，如果不是给老师写报告，只是搞搞重命名应该够用了，还没有WPS的弹窗😨

以及，因为[excel][libre_office_homepage]或者[nexus file][nexus_file_homepage]这类软件对于编号式重命名方面的功能非常强大，本批处理以后也不会在这方面增加功能。

#### 使用

直接打开后会弹出全提示模式，使用方法详见提示信息：

```batch
echo ^[警告^]这里若不退出，下一步将进行重命名
echo 请确认已做好文件备份，以防止意外情况发生
echo.
echo ^[警告^]请确保不要使用任何windows
echo 文件系统禁止使用的符号进行重命名
echo.
echo 全提示模式：
echo.
echo 1.待改名文件在当前路径下的work文件夹内
echo.
echo 2.work文件夹内所有文件都会被重命名
echo.
echo 3.改名后文件名列表dst_list.txt处在当前路径下，
echo   请使用GB2312编码txt，否则会有乱码
echo   (我大窗国自有窗国情在此)
echo.
echo 4.dst_list.txt的文件名列表格式为：
echo   1)一行一个文件名
echo   2)顺序不影响重命名
echo   3)文件名中可以包含空格
echo.
echo 5.输出这段提示信息前，
echo   如果你的work文件夹已存在，
echo   批处理已将其中的文件名输出成列表
echo   到当前路径下的src_list.txt中
echo.
echo 6.请根据自己喜好创建dst_list.txt，
echo   因为下一步程序
echo   1) 不会再改变dst_list.txt
echo   2) 根据src_list.txt和dst_list.txt进行重命名
echo      如果你有特殊需要，可以对src_list.txt中的文件名
echo      进行编辑操作
echo.
echo 7.不会提示给予再次确认改名前后名称对应关系，
echo   改名前请做好文件备份，以免出现意外情况
echo.
echo 8.建议使用excel提前编辑好改名后文件名
echo   并拷贝到dst_list.txt中
echo   注意使用Ctrl-H搜索替换掉excel特有大空格
echo.
echo 9.不会更改扩展名
echo.
echo 10.如果你做好了1-4的准备，再重新运行本批处理
echo    将会进入到另一个重命名模式
echo.
echo 11.重命名之后
echo    src_list.txt和dst_list.txt不会自动删除
```

另一种模式其实跟这个差不多，但是会“自动”帮你把dst_list.txt进行排序，未必是好事，后续会改进这个逻辑。提示信息如下：

```batch
echo ^[警告^]这里若不退出，下一步将进行重命名
echo 请确认已做好文件备份，以防止意外情况发生
echo.
echo ^[警告^]请确保不要使用任何windows
echo 文件系统禁止使用的符号进行重命名
echo.
echo 核对模式：
echo.
echo 1.为了防止你的排序方法
echo   和batch文件名顺序有不一致情况，
echo   已对新文件名列表
echo   按照文件名的顺序重新进行排序，
echo   但是这不代表两种文件顺序
echo   就一定一一对应
echo.
echo 2.^[警告^]如果新旧文件名差异较大，
echo   建议逐行核对
echo.
echo 3.下一步程序
echo   1) 不会再改变dst_list.txt
echo   2) 根据src_list.txt和dst_list.txt进行重命名
echo      如果你有特殊需要，可以对src_list.txt中的文件名
echo      进行编辑操作
echo.
echo 4.重命名之后
echo    src_list.txt和dst_list.txt不会自动删除
```

### 批量压缩批处理\(7z_batch和run_7z_batch\)

这个批处理其实意义不大，正常的用途中绝不会有人想到要让每个文件都只打包成一个文件，多数情况下大家都是为了避免小文件传输影响速度或者便捷性才会使用压缩把多个文件打包成一个大压缩包，而且对于有损视频格式而言，使用压缩算法可以再压缩出的空间微乎其微，打成一个大的压缩包会因为体积太大，而不利于大家下载，完全就是做重复计算浪费性能和电费。

做这样的批处理完全是迫于百度云对特定文件格式的检测，规避百度云的所谓检测删封的同时方便大家索取单个视频文件而已。

这个程序其实本来可以写的挺简单的，主要是考虑到要设置一些需要忽略的情况，譬如如果用户非要在待压缩文件所在文件夹里面启动批处理进行压缩，但又不想进行多余的操作，把批处理自身也压缩，产生不必要的文件，那么就需要设置忽略的脚本名称。

其实这个批处理的提示信息也写得挺详细的了，看提示信息基本就会用了。

```batch
echo 本批处理可以将某一文件夹内的文件逐个压缩
echo.
echo 首先确认命令行7z，也就是7z.exe是否添加到环境变量-系统变量
echo 或者确认7z.exe在待压缩文件所在文件夹
echo.
echo 输入待压缩的文件所在文件夹
set /p work_dir=(默认为当前文件夹，回车为默认):
echo.
if not defined work_dir set work_dir=%~dp0

echo 输入压缩后的压缩格式后缀(包括点)
set /p dst_exte=(默认为.7z，请输入7z支持的压缩格式，回车为默认):
```

还有一个run_7z_batch，是我考虑到这个程序一定要有自定义输入，但是如果由程序提问等待用户输入这样太麻烦了，等于是我每次都要重新输入参数，run_7z_batch就是在命令行界面下调用7z_batch，将参数直接传递给7z_batch，这样7z_batch就不提问了，直接运行更加省事。

因为run_7z_batch是使用call命令调用7z_batch运行，我没查到批处理能获得到call它的批处理或者程序的名称的功能，所以这多设置了一个参数，传递给7z_batch，告诉它run_7z_batch的名字是什么，这样来忽略额外的文件名。还有就是，我在7z_batch里面也把对自身文件名的获取设置成从命令行参数中得到，这样的话就对用户更改了批处理文件名的情况做出了处理。换句话说，你在使用这两个批处理的时候，可以把它们的名字命名成任意你喜欢的名字，也不会影响程序对文件的正常压缩过程，虽然我觉得很没有必要就是了。

```batch
set z7_bat_name="7z_batch.bat"
rem 7z_batch文件名
set work_path="C:\userfile\Desktop\压制\batch脚本\test\work"
rem 待压缩文件所在文件夹，即工作文件夹
set run_bat_name="run_7z_batch.bat"
rem 需要额外忽略的一个文件名，若此脚本在工作文件夹内，则需要忽略
```

### python环境批处理

github链接：[bingling batch python syspath][bingling_batch_python_syspath]

其中win_py_syspath_sw_create.bat为python环境切换创建批处理，win_py_syspath_sw.bat为python环境切换批处理，win_py_syspath_query.bat为系统环境变量查询批处理。

该批处理编写时用到的参考资料：

[bat知识点3\_for循环\_跳出嵌套 - haibo19981的专栏 - CSDN博客](https://blog.csdn.net/haibo19981/article/details/52251945)

[批处理 FOR参数/F之tokens详解\_DOS/BAT\_脚本之家](https://www.jb51.net/article/17928.htm)

[Set windows environment variables with a batch file - Stack Overflow](https://stackoverflow.com/questions/21606419/set-windows-environment-variables-with-a-batch-file)

[如何在cmd命令行中查看、修改、删除与添加环境变量 - wzsbll的专栏 - CSDN博客](https://blog.csdn.net/wzsbll/article/details/6690895)

[SET和SETX命令的应用 - baiyibin0530的专栏 - CSDN博客](https://blog.csdn.net/baiyibin0530/article/details/78841653)

[通过注册表设置环境变量 \- anhuidelinger的专栏 - CSDN博客](https://blog.csdn.net/anhuidelinger/article/details/14044653)

[bat、cmd 批处理中（或 DOS环境）的特殊字符 - jinzhenshui - 博客园](https://www.cnblogs.com/jinzhenshui/archive/2012/05/17/2506129.html)

[cmd - How to get last n tokens from string using "FOR /F" in batch file - Stack Overflow](https://stackoverflow.com/questions/35477290/how-to-get-last-n-tokens-from-string-using-for-f-in-batch-file)

[批处理：FOR的参数/F之delims详解 - kukou的专栏 - CSDN博客](https://blog.csdn.net/kukou/article/details/4895676)

[regex - printing all tokens after 2nd token in a batch script - Stack Overflow](https://stackoverflow.com/questions/17327512/printing-all-tokens-after-2nd-token-in-a-batch-script)

[在BAT文件中实现对空格分割的字符串的处理 - zhifeng - ITeye博客](https://alizf.iteye.com/blog/616388)

[.bat批处理（六）：替换字符串中匹配的子串 - AlbertS Home of Technology - CSDN博客](https://blog.csdn.net/albertsh/article/details/79919465)

[command line - String replacement in batch file - Stack Overflow](https://stackoverflow.com/questions/2772456/string-replacement-in-batch-file/2772498)

[string - Batch - replacing with percent symbol - Stack Overflow](https://stackoverflow.com/questions/41323488/batch-replacing-with-percent-symbol)

### 其他批处理

一个是getname_batch还有一个是test_rename_batch，前面的看到代码中的注释就知道是怎么用的了，后面这个是用来测试rename_batch的批量生成txt的批处理，没必要拿来用我就没加任何注释，但是稍微懂一点batch应该也可以看懂，这里就不再解释了。

[E801148]: https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/%E5%86%B0%E7%81%B5win%E6%89%B9%E5%A4%84%E7%90%86/[Crappy%201080P]%20Code%20Lyoko%20S4E80_001148.878.png
[bingling_batch_github]: https://github.com/BingLingGroup/bingling-batch
[download_batch_zip]: https://github.com/BingLingGroup/bingling-batch/archive/dev.zip
[nexus_file_homepage]: http://www.xiles.net/
[bili_space]: https://space.bilibili.com/3512816
[windows_batch_docs]: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands
[libre_office_homepage]: https://www.libreoffice.org/
[bingling_batch_python_syspath]: https://github.com/BingLingGroup/bingling-batch/tree/dev/python_syspath_batch
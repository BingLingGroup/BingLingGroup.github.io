---
layout:     post
title:      aegisub使用指南(210624)
date:       2019-08-02 18:00:00
author:     "冰灵"
categories:
    - 演示
tags:
    - 教程
    - 字幕
    - 时间轴
    - aegisub
    - x264
    - 压制
    - Premiere
    - 帧服务器
thumbnail: "http://static.aegisub.org/img/logo-large-bcf2435c.png"
---
>题图来源<escape><a name = "ref_1_s"><a href="#ref_1_d"><sup>[1]</sup></a></a></escape>
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。
>标题后面括号里的日期指的是最后更新日期，头像旁边的日期是最初发布日期。

<escape><font size=4>目录</font></escape>

1. [下载软件](#下载软件)
2. [软件初始设置](#软件初始设置)
   - 2.1 [Win10系统DPI缩放](#win10系统dpi缩放)
   - 2.2 [Aegisub默认选项调整](#aegisub默认选项调整)
     - 2.2.1 [颜色标准](#颜色标准)
     - 2.2.2 [样式入门](#样式入门)
     - 2.2.3 [特效入门](#特效入门)
3. [加载视频和音频](#加载视频和音频)
4. [打轴](#打轴)
   - 4.1 [视频区打轴](#视频区打轴)
   - 4.2 [音频区打轴](#音频区打轴)
5. [翻译](#翻译)
6. [压制](#压制)
   - 6.1 [作为mov导入非编](#作为mov导入非编)
   - 6.2 [使用帧服务器-avisynth压制](#使用帧服务器-avisynth压制)
7. [其他](#其他)
8. [注释](#注释)

### 下载软件

[下载地址](https://aegi.vmoe.info/downloads/)

完整版为安装包版本，便携版为免安装的版本，如果是windows系统，下载32位版本，建议使用安装包版本。

### 软件初始设置

#### Win10系统DPI缩放

<escape><div title="属性-兼容性" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/aegisub_guide/properties-compatibility.png" height="60%" width="60%"></div><div align="middle">属性-兼容性</div></br><div title="更改高DPI设置" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/aegisub_guide/properties-compatibility-change-dpi.png" height="60%" width="60%"></div><div align="middle">更改高DPI设置</div></escape>

属性-兼容性-更改高DPI设置-替代高DPI缩放行为-应用程序。
这样能让软件显示更加清楚。

### Aegisub默认选项调整

#### 颜色标准

打开Aegisub，选择菜单栏查看-选项，选择左侧高级-视频一栏，取消选择`强制BT.601`，现在越来越多的视频都是原生720P以上的了，原生720P以上的视频建议用BT.709，否则会有色差。

#### 样式入门

参见[官方教程](https://aegi.vmoe.info/docs/3.2/Styles/)，个人建议为避免侵权，请使用这些[商用免费字体](https://zhuanlan.zhihu.com/p/27302723)，个人推荐思源宋体和思源黑体。

好看的样式一般为，字体主要颜色为白色或亮色，边框颜色为黑色或暗色，无阴影，不会调色的推荐用android应用（酷安）MD配色参考，或者是[网页版material design取色器](https://material.io/resources/color)。

至于以下两种搭配，一是较大的字重配合较细的边框，二是较小的字重配合较粗的边框，可根据自己的喜好自行选择。不过我个人是推荐使用部分透明的厚边框搭配较小字重使用，譬如厚度达到或超过4像素，透明度90，字重为medium甚至更小。

如果喜欢模糊特效的，可以通过菜单栏-自动化-添加边角模糊，`Ctrl-A`全选，然后再`Ctrl-H`将`{\be1}`标签全部替换成`{\blur4}`以达到效果。`blur`的模糊感比`be`更好，这里只是借助脚本批量添加特效而已。如果对选择对象有疑虑的，可以考虑使用菜单栏-字幕-选择多行功能。

#### 特效入门

续上，如果喜欢有模糊阴影特效的，aegisub不能直接添加带模糊的阴影，但是可以曲线救国，复制相关字幕行，将边框调至0，主要颜色调为你需要的阴影颜色，然后加`{\blur}`标签，这样即可达到字体本身模糊而非边框模糊的效果。

为了和普通字幕有一定位移差距，可以添加`{\pos}`标签来控制位置，同时`{\pos}`标签也可以通过视频区最左一列向下第二个拖放字幕按钮控制。注意位置的控制和行对齐方式`{\a}`有关。

正常情况下渲染器是不允许字幕重叠的，除非添加了自定义`{\pos}`标签，或者添加了层次编号。在添加了`{\pos}`标签不加层次编号的情况下，其图层上下是以字幕在字幕行位置的先后顺序来控制的，换句话说字幕行位置越靠前，图层越靠下。

<escape><div title="层次编号" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/aegisub_guide/layer-number.png" height="80%" width="80%"></div><div align="middle">层次编号</div></escape>

层次编号也是类似的，层次编号在文本区最左边，0为最底层，数字越大层越靠上。相关的特效标签详细描述，包括一些匀速运动效果的制作，可以参考ass[特效标签](https://aegi.vmoe.info/docs/3.2/ASS_Tags/)。以及很重要的[卡拉OK特效制作](https://aegi.vmoe.info/docs/3.2/Karaoke_Timing_Tutorial/)。

### 加载视频和音频

选择菜单栏视频-打开视频，选择视频文件打开。

<escape><div title="界面一览" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/aegisub_guide/overview.png" height="80%" width="80%"></div><div align="middle">界面一览</div></escape>

打开之后的界面如图所示，左上为视频区，右上为音频区，音频区下方为文字编辑区，文字编辑区下方是字幕栏。这里我们需要知道一个概念叫做焦点，如果你之前动过音频编辑区中的按键，那你的焦点就停留在音频区，无法使用别的区的快捷键，其他的也是类似。

<escape><div title="音频区" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/aegisub_guide/audio-view.png" height="80%" width="80%"></div><div align="middle">音频区</div></escape>

音频区建议打开频谱分析模式，而不是波形图模式。频谱分析模式的按钮在右下角从右到左第三个，这样查看人声区域更为直观，而波形图可能会把人声和其他声音看混。

注意保存！虽然该软件每隔60秒就会自动保存一次，但是不包含自动恢复功能（需要自己去`C:\Users\你的用户名\AppData\Roaming\Aegisub\autosave`下找，或者在菜单栏查看-选项-备份中自己选择自动保存目录），我建议定期使用`Ctrl-S`快捷键进行保存。

所有快捷键都可以在选项-热键中修改，如果对以下介绍的快捷键不爽可以自己改。

### 打轴

打轴主要有两种方式。

视频区打轴主要是面向视频画面的打轴，效率较低，建议只在特殊情况下使用。

音频区打轴效率较高，建议作为主要的对话字幕的打轴方式。

还有一种邪典打轴是先使用软件自动生成时间轴，再作调整，这方面比较便利的工具是subtitleedit，右键subtitleedit的音频区就可以找到一个猜测时间码，然后自动生成时间轴，如果不愿意在subtitleedit编辑字幕，也可以导出成srt或者ass再用aegisub来编辑。另外一个在自动探测时间轴上更准确的工具是autosub ，中文版的[使用说明](https://github.com/BingLingGroup/autosub/blob/dev/docs/README.zh-Hans.md)，只要输入-i xxx参数即可自动生成时间轴。（生成时间轴均是本地生成，不需要联网）

subtitleedit真正强大的地方在于可以OCR各种硬字幕，大家如果有需求可以深入研究。

对话字幕的打轴标准是，一行字幕不要过长，导致左边视频区的字幕发生折行现象。如果折行不是很明显，可以在字幕内容最前部分添加标签`{\fs}`。如果实在太长，请根据实际语意分句，后方音频区打轴会介绍分句的操作。

#### 视频区打轴

<escape><div title="视频区" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/aegisub_guide/video-view.png" height="80%" width="80%"></div><div align="middle">视频区</div></escape>

视频区从左到右第9个按钮，是将当前视频区的时间，设置成当前字幕的起始时间`Ctrl-3`。

第10个则是设置成结束时间`Ctrl-4`。有时候根据视频定位还是很有用的，譬如做那些字幕组常见的对场景的操作。在这种情况下，保持焦点在视频区这边，然后用鼠标滚轮可以按帧细调时间，非常方便对场景。

左边两个按钮则刚好相反，是让视频界面的时间，设置成字幕的始/末时间，快捷键分别是`Ctrl-1`和`Ctrl-2`。

当前字幕指的是当前字幕区选中的字幕，这里推荐将选项-视频里的`选择行改变后，视频位置变为所选行的开始时间`这一项取消了勾选，意味着原先单击就会改变视频位置，现在需要双击，这样可以方便我们在不需要改变当前活动行或者说当前视频位置的时候，单击别的行更改别的行的文字。

<escape><div title="视频区下方" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/aegisub_guide/video-view-buttons.png" height="80%" width="80%"></div><div align="middle">视频区下方</div></escape>

至于视频区下方的控件，第一个播放按钮就是播放视频`Ctrl-P`，第二个则是播放字幕行内视频`Home`，建议修改为自己习惯用的按键。

#### 音频区打轴

<escape><div title="音频区下方" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/aegisub_guide/audio-view-buttons.png" height="80%" width="80%"></div><div align="middle">音频区下方</div></escape>

对音频区的编辑，需要用到的快捷键主要有这三个。

- R播放所选部分音频区间，对应上图左至右第二个按键。
- E播放所选部分头500毫秒，对应上图左至右第六个按键。
- D播放所选部分尾500毫秒，对应上图左至右第七个按键。

如果焦点不在音频区，请用鼠标点击这一栏中的按键完成操作。
注意默认生成新行的计时长度，可以在选项-音频中进行调整。

一种使用方法是左手食指D键，中指R键，无名指E键控制音频播放，右手鼠标控制始末时间。

注意拖动时按左键和不拖动按左键的行为不一样，不拖动按左键是控制开始或者结束时间，但是拖动时按左键会让上一个结束时间成为开始时间，当前位置成为结束时间。右键没有这个逻辑，如果用不到这个逻辑，建议取消勾选选项-音频-左键点击拖动动作结束标记。

注意编辑信息只有回车提交改动后才会保存，所以这段时间内不要切换到视频区。当一行时间轴制作完毕后，右手回车确认当前行，然后跳到下一行字幕。

如果对时间轴的长句断句效果不满意，可以有两种方式重新分句，一种是将原本在剧本中的长句对应的多行字幕选中(多选请按住`Shift`键或者`Ctrl`键，效果不同)右键-合并(连接J)，然后根据自己的喜好将光标放在下半句的第一个词前面，右键-在光标处分割(概略计时)，如不满意再根据此结果微调。另一种则是直接拖动音频区开始结束时间进行调整，如果行数不够可以通过选中右键-插入(之后)来增加。

如果要中途插入时间轴，那么选择最下方的字幕栏区域，根据你当前行的时间位置，右键选择插入(之前)或者插入(之后)，然后在新生成的字幕行中重复以上分句操作。

### 翻译

如果是制作双语字幕，翻译前首先确认是否复制了时间轴，如果没有，点中字幕栏中任意一行字幕，使用快捷键`Ctrl-A`全选所有行字幕，使用`Ctrl-C`复制，然后选择最下面的空行，使用`Ctrl-V`粘贴，这样就获得了中文字幕的时间轴。如果没有空行，请选择最后一行后右键插入之后来添加一行，或者回车也可以。

翻译时，可以在文字编辑区删除原文这样来进行翻译，不过我不太推荐。更好的方式则是选择菜单栏字幕-翻译助手，进行翻译，借助翻译助手的快捷键，翻译效率会更高一些。

### 压制

字幕做好以后就是压制。如果你是普通搬运工，已经有生肉的情况下，不需要加特效那些必须要非编实现的东西，那么直接使用小丸工具箱压制即可，相关教程参见[磁爆线圈X的文章](https://www.bilibili.com/read/cv311967)。

以下主要讲解较为冷门的，两种配合非编使用，输出带字幕视频的方法，一般多用于原创类视频压制。

- 因为制作ass字幕时必须要有视频，所以你在正式输出带字幕的视频之前，肯定已经输出了一版不带字幕的视频了。这里介绍的方法则是从非编中只经过一次压制出来的带字幕视频的压制方法（俗称直出），而非在用于aegisub读取的无字幕视频上再压制得到的带字幕视频的压制方法（俗称二压，画质损失会比前者大）。当然这也暗示了你可以在第一版不带字幕视频上面用较差参数获得较快输出的速度，~~反正也不是用在最终视频上面画质差一点无所谓。另行参考：画质大敌[消极压制](https://github.com/zyzsdy/NegativeEncoder)。~~

#### 作为mov导入非编

如果是作为mov导入非编，想要在非编里面把字幕压制上的，而不是通过帧服务器的，推荐使用[ffmpeg的一条指令](https://www.zhihu.com/question/42359025/answer/277296784)来压制含透明通道的字幕视频。原理：通过lavfi生成mov封装的png视频流格式，参见[stackoverflow](https://stackoverflow.com/questions/46315483/ffmpeg-create-a-transparent-background-with-lavfi)以及ffmpeg官方的[ffmpeg-filters文档](https://ffmpeg.org/ffmpeg-filters.html)。

```bash
ffmpeg -y -f lavfi -i "color=color=背景色:rate=帧率:size=尺寸,format=rgba,subtitles=字幕文件名:alpha=1" -c:v png -t "hh:mm:ss.000" 目标文件名.mov -stats
```

- 背景色：空白视频的背景颜色，透明的背景可以使用`0xFFFFFF00`，颜色格式[参考](https://ffmpeg.org/ffmpeg-utils.html#color-syntax)。注意，虽然表面上看任何透明度设置为00的背景都为透明，但实际上在字体边缘会出现非透明色，而非透明色即为透明度值以外所设置的颜色，如0xFFFFFF为白色。所以正常情况下还是建议生成绿幕mp4视频，并用色键/超级键之类的功能进行抠图后使用，这样不会有色边问题困扰。如果字幕边缘色，如边框以及阴影，只有一种，那么可以考虑设置为字幕边缘颜色，如字幕边缘颜色为黑色的情况下，设置为0x000000000。
- 帧率：整数或者整数相除形式如`24000/1001`（23.976fps即NTSC）。这会直接影响到字幕特效的流畅度，建议至少达到你要导入的项目的帧率。
- 尺寸：类似`1920x1080`的形式。
- 字幕文件名：如果有空格，请用单引号包围。
  - 暂时没找到填写绝对路径的方法，建议填写当前路径的文件。
  - 或者说在文件浏览器下使用`Shift - 左键`从当前文件夹打开Powershell后使用。
- hh:mm:ss.000：小时：分钟：秒.毫秒，这个需要自己根据最晚一行字幕的时间填写，是空白视频的持续时间，至少应该达到你的字幕的持续时间，ffmpeg不会帮你判断你的字幕有多长时间。
- 目标文件名：如果有空格，请用引号包围。

而ffmpeg的安装建议使用[chocolatey](https://chocolatey.org/install)，这样可以把ffmpeg加到环境变量里面，可以在任意目录使用。

安装时的命令为：

```bash
choco install ffmpeg -y
```

请使用管理员权限打开cmd或者powershell后输入安装命令。

Vegas导入mov后，记得在mov文件-属性-媒体-Alpha通道中，修改为`直接(非蒙版的)`即可。注意如果有色差，是vegas自己的问题，需要在项目属性中确保：

- 像素格式 - `32-bit浮点（全范围）`
- gamma合成量 - `2.222（视频）`
- 查看转变 - `关`

#### 使用帧服务器-avisynth压制

推荐通过小丸工具箱配合使用，压制参数和相关教程参见[磁爆线圈X的文章](https://www.bilibili.com/read/cv311975)，搜索关键词`帧服务器`即可跳转到。注意vegas使用的帧服务器则是debug mode frameserver。

主要是通过avs挂载字幕压制来做到的，在遵循前面的文章，打开小丸工具箱的avs界面准备填语句时，改成以下即可。

```python
plugin_source_name = "小丸工具箱父目录\小丸工具箱236\tools\avs\plugins\VSFilter.DLL"
video_source_name = "视频文件"
ass_source_name = "字幕文件"

LoadPlugin(plugin_source_name)
AVISource(video_source_name)
ConvertToYV12(matrix = "Rec709")
textsub(ass_source_name)
```

注意该教程还有[上篇](https://www.bilibili.com/read/cv311967)，上篇中的防二压参数对于大会员画质（分辨率不超过1080P，帧率30fps+或码率3000kbps-6000kbps）依然有效。

虽然原作者只给出了在设置-自定义命令行来定义2pass参数的使用方法，但是我们也可以用在小丸工具箱前面的自定义模式下面自己创建CRF模式下的参数（当然CRF模式比较难控制码率，这个根据个人喜欢来使用），方法是将其参数复制下来之后，在视频-自定义模式下填入参数，然后按照个人喜好再加`--crf xx`即可，注意crf的值不要超过23，crf的值超过23画质损失就比较明显了，动态视力好的人可能就能发现了，传b站crf的值也不建议低于21，除非你的视频静态画面特别多，甚至是PPT的那种。

注意不要轻信网上说的高压参数，这个世界上只有妥协压制没有真正的高压参数，即使是h265或者说HEVC也只能做到比h264高30%的效率而已（虽然现在b站还不支持）。或者换句话说磁爆线圈X的这套参数基本已经是对硬件要求比较高的情况下可以允许的最好的高压参数了，其他参数调了可能还会被b站二压，自己用倒无所谓，特别是他这套参数还是对b站进行优化的。

以及，帧服务器的音轨要单独压制，可以用非编单独输出aac/flac音频，然后用小丸封装/压制后再封装。

注意Vapoursynth不支持这种玩法。至少我没发现，有谁知道的可以分享出来。

### 其他

由于b站对1080P30fps以下且3000kbps以下的视频采取无条件二压，如果有人想要通过强行提帧率的方式而非提码率的方式进入大会员领域从而变相防止二压，可以了解一下[SVP补帧技术](https://lolicon.link/2017/02/11/using-svp4-in-video-processing/)，注意如果使用帧服务器源的avs似乎不能再套avs版的SVP，好像会炸，当然机器好的也可以试试。

这里推荐用Vapoursynth（二压就二压吧，补帧要紧.jpg）+SVP的方法，Vapoursynth套字幕建议使用Vapoursynth版vsfilter，~~在nmm的一个角落里可以下载到~~[github上有](https://github.com/sorayuki/VSFilterMod/releases)。

Vapoursynth的使用方法，建议参考[VCB-S教程专栏](https://vcb-s.nmm-hd.org/)，或者去官网查文档。

当然实际上用非编的话，也可以假补帧，通过关闭帧数重采样，但是输出超过30帧视频的方式。虽然这样有点浪费码率，但是对于字幕效果还是有加成的，你的字幕会按照高帧率的画面进行渲染，一些特效动画会更加细腻。

附：

我的SVP Vapoursynth参数是（个人已调整至最优，不太建议改动，除非你知道自己在做什么）：

```python
import vapoursynth as vs
import mvsfunc as mvf

core = vs.get_core()

# 把这俩 DLL 拷贝到 VapourSynth\plugins64 先
# core.std.LoadPlugin("libsvpflow1_vs64.so")
# core.std.LoadPlugin("libsvpflow2_vs64.so")

svp_frame_num = 50
svp_frame_den = 1

source_file = r"视频文件"
sub_file = r"字幕文件"
# 不要删掉r，r表示Python原始字符串，这样可以在r修饰的字符串里面填写反斜线

# source_0 open
clip = core.lsmas.LWLibavSource(source=source_file, format="yuv420p8")

# 运动向量精度 0.5 像素
# 使用 GPU 渲染
# 放大使用 Wiener interpolation(类似 Lanczos 6tap)
# 缩小使用类似 BicubicResize(b=1,c=0) 的 cubic filter
super = core.svp1.Super(clip, "{scale:{up:2, down:4}, pel:2, gpu:1}")
# 使用 GPU 渲染
# 搜索的运动矢量的方向时包含前向后向
# 搜索的块大小 = 32x32 每个方向重叠四分之一个块
# 精细搜索使用彻底搜索
# 粗略搜索使用六边形搜索
vectors = core.svp1.Analyse(
    super["clip"],
    super["data"],
    clip,
    "{gpu:1, vectors:3, block:{w:32, overlap:3}, main:{type:4, search:{coarse:{type:2, distance:-6, bad:{sad:2000, range:24}}}}, refine:[{thsad:250}]}")
# 渲染算法 =
#    时间加权之下混合前向和后向部分运动向量补偿 +
#    额外的遮罩减小光晕提升物体边缘线条质量 +
#    额外的运动向量进一步减少光晕
# 帧插补 = 自动判断
smooth = core.svp2.SmoothFps(
    clip, 
    super["clip"], 
    super["data"], 
    vectors["clip"], 
    vectors["data"],
    "{{gpuid:0, rate:{{num:{sfn}, den:{sfd}, abs:true}}, algo:2, mask:{{area:200}}, scene:{{mode:3}}}}".format(sfn=svp_frame_num, sfd=svp_frame_den))

smooth = core.std.AssumeFPS(
    smooth,
    fpsnum=smooth.fps_num,
    fpsden=smooth.fps_den)

smooth = mvf.Depth(smooth, depth=10)
# 添加字幕时使用10bit色深，觉得没用可以改回8bit
ass_out = core.vsfm.TextSubMod(clip=smooth, file=sub_file)
# 注意这里字幕文件添加位置在补帧之后，补帧之前添加字幕会污染画面
ass_out = mvf.Depth(ass_out, depth=8)
ass_out.set_output()
```

### 注释

点击上箭头字符可返回原位置，方括号中的数字表示引用的次序。
<escape><a name = "ref_1_d"><a href = "#ref_1_d">[1]</a></a></escape> <escape><a href = "#ref_1_s">↑</a></escape> <escape><a href = "http://www.aegisub.org/">aegisub官网</a></escape>

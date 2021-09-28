---
layout:     post
title:      【每日宇航员/翻译】Starship为什么要做机腹向下机动
date:       2021-4-27 12:00:00
author:     "旋火"
categories:
    - 转载
tags:
    - 航天
    - 火箭
    - Everyday Astronaut
    - Starship
    - SpaceX

thumbnail: https://everydayastronaut.com/wp-content/uploads/2021/04/maxresdefault.png
---
> 这篇文章来自旋火的投稿，是同名视频内容的文字版。
> [原文章出处](https://everydayastronaut.com/starships-belly-flop-maneuver/)，[原视频出处](https://youtu.be/BqJ5bKuApbs)，[翻译视频出处](https://www.acfun.cn/v/ac28275850)，翻译时有一定删改。
> 原文作者：Everyday Astronaut
> 原文标题：Starship and its Belly Flop Maneuver
> PC版网页左上角从上到下第二个图标是目录，请多用目录。
> 网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。

<escape><font size=4>目录</font></escape>

1. [序](#序)
2. [Starship从机腹向下到机尾向下的机动](#Starship从机腹向下到机尾向下的机动)
   - 2.1 [推进剂沉在Starship的机腹位置](#推进剂沉在Starship的机腹位置)
3. [火箭着陆时的终端速度](#火箭着陆时的终端速度)
   - 3.1 [Starship的终端速度](#Starship的终端速度)
   - 3.2 [Starship与猎鹰9号的对比](#Starship与猎鹰9号的对比)
4. [推重比](#推重比)
   - 4.1 [回到悬停](#回到悬停)
   - 4.2 [着陆节流](#着陆节流)
   - 4.3 [使用汽车的刹车模拟节流](#使用汽车的刹车模拟节流)
   - 4.4 [使用汽车的油门模拟节流](#使用汽车的油门模拟节流)
5. [着陆过程中的重力损失](#着陆过程中的重力损失)
   - 5.1 [越来越高](#越来越高)
6. [不同高度下Starship的翻转](#不同高度下Starship的翻转)
   - 6.1 [不同的翻转高度选择](#不同的翻转高度选择)
7. [翻转过程中的乘员状态](#翻转过程中的乘员状态)
   - 7.1 [会受到多少过载力](#会受到多少过载力)
8. [总结](#总结)

### 序

作为一枚宽9米，高50米的火箭，Starship正在进行从未尝试过的机动，即其会从空中水平落下，然后翻转并垂直着陆。

到目前为止的着陆尝试带来了很多问题。

- 为什么要机腹向下？
- 为什么要在离地面这么近的地方做翻转机动？
- 这对载人来说是否足够安全？
- 他们为什么不早点开始翻转机动，以确保有足够的时间在出错时进行修正？
- 其经历的过载力是否合理？
- SpaceX是否应该改用猎鹰9号一级的着陆方式？

本文将讨论影响Starship着陆机动的不同方面。

- 着陆时的发动机组合的不同选择
- 终端速度
- 重力拖拽
- 推力与重量比
- 发动机节流

### Starship从机腹向下到机尾向下的机动

Starship的着陆机动是一种新的，独特的火箭着陆方式。一开始，Starship以机腹朝前的姿态从空中落下，在自由落体的情况下，尽可能地消除最多的速度。在大约0.5km的高度，它将点燃两台猛禽发动机，并使之完全摆动，同时折起后翼面，并将机身姿态从水平方向摆动到垂直方向，这样它就可以以机尾向下的姿态，使用着陆腿进行着陆。

当后翼面收起时，与尾部相比，机头部分经历的阻力大大增加。这与猛禽发动机的点火相结合，让机尾在机头下旋转，使火箭垂直。未来，SpaceX可能会给Starship添加热气推进器来进一步帮助旋转。

由于Starship水平点燃猛禽发动机，发动机必须从被称为头部储罐的特殊储罐中抽取推进剂。这是因为发动机不能吸收任何空气。如果在这种姿态下，继续从主储罐中吸收液态甲烷（CH4）和液态氧（LOX），发动机最终会吸入空气，这可能会导致发动机的快速意外解体（RUD）。

<escape><div title="Starship储罐内部结构。（作者：C-Bass Productions）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_04_37_24.Still001-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">Starship储罐内部结构。（作者：C-Bass Productions）</div></escape>

#### 推进剂沉在Starship的机腹位置

由于火箭的水平方向，推进剂沉淀在Starship的腹部，或者说迎风一侧。这是因为火箭被不断变厚的大气层所减缓，从而将推进剂压在腹部。

由于从储罐到猛禽发动机的推进剂管路位于火箭底部，在机腹翻转期间，如果发动机试图从主储罐中抽取推进剂，就会抽到大部分空气。而液氧头部储罐位于机头部分，液态甲烷头部储罐位于Starship的两个主储罐之间，这俩头部储罐几乎保持满载，直到着陆机动。头部储罐的排液阀甚至安排了一点小的角度，以利于在腹部向下时仍能抽取到推进剂。

在水平方向点燃发动机会产生大量的水平速度，随后火箭会有意地过度翻转以抵消其增加的水平速度。

### 火箭着陆时的终端速度

机腹向下机动的一个目的是为了尽可能多地被动地减少速度。另一个目的是控制Starship在轨道再入时的姿态和峰值温度。一般来说，火箭的终端速度越低，就必须越晚进行着陆点火，因为不再需要消除那么多速度。

#### Starship的终端速度

终端速度的定义是：物体在空气等流体中下落时达到的最大速度，或者说是当向下的力或重力等于阻力时的速度。终端速度随着物体周围条件的变化而变化。当气压增加，大气层变厚时，终端速度会变慢，因为物体会遇到更多的阻力。

Starship的机动可以与跳伞运动员在自由落体时的动作相比较。当跳伞运动员腹部朝前时，他们的身体受到的阻力最大，此时终端速度是最低的。如果姿态改成脚或头朝前，那么跳伞者遇到的可供减速的空气的表面积就会小得多（也就是参考面积会小很多）。

<escape><div title="Starship以机腹朝前的姿态下落，此时其重力等于空气阻力。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_07_13_19.Still002-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">Starship以机腹朝前的姿态下落，此时其重力等于空气阻力。（作者：每日宇航员）</div></escape>

同样，Starship有能力改变其姿态，并因此根据翼面向外伸展的程度来改变终端速度。在这种情况下，翼面类似于跳伞运动员的胳膊和腿。如果翼面伸展得更多，航天器上的阻力将增加，如果翼面折叠了起来，阻力将减少，从而使终端速度更快。因此，猎鹰9号一级与Starship的下降过程存在明显的差异。猎鹰9号在大气层中下降的速度比Starship高得多，因为其以发动机朝前的姿态下，增加阻力的表面积较小。

#### Starship与猎鹰9号的对比

来自flightclub.io的德克兰·墨菲（Declan Murphy）制作了一系列火箭发射的高度精确模拟，当然他也制作了Starship下降段的模拟。Flight Club把SN8的飞行轨迹与猎鹰9号的NROL-108任务进行比较。模拟显示，SN8的最大下降速度是150m/s，然后，由于大气层不断变厚，减慢到只有90m/s。这样较低的速度一直保持到翻转机动之前，足以使之进行安全降落。

<escape><div title="猎鹰9号和Starship在着陆点火开始后的速度比较。（作者：德克兰·墨菲和每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_11_49_12.Still004-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">猎鹰9号和Starship在着陆点火开始后的速度比较。（作者：德克兰·墨菲和每日宇航员）</div></escape>

另一方面，猎鹰9号的着陆速度要快得多。即使猎鹰9号的初速度更高，但因为从更高的高度开始下落，所以它到达终端速度310m/s时的高度要比Starship高不少，同时其终端速度也比Starship高不少，因为产生阻力的表面积更小（译者注：更严谨地说，套用终端速度的公式，是质量与参考面积的比除以阻力系数的值相对更大，假设两者所处的大气密度接近）。一旦到达终端速度，猎鹰9号将开始着陆点火。

<escape><div title="Starship水平与垂直姿态下的表面积（参考面积）。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_08_53_06.Still003-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">Starship水平与垂直姿态下的表面积（参考面积）。（作者：每日宇航员）</div></escape>

<escape><div title="终端速度公式。（作者：维基百科终端速度词条）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/终端速度公式.png" height="40%" width="40%"></div></escape>
<escape><div align="middle">终端速度公式。（作者：维基百科终端速度词条）</div></escape>

相比于轨道速度7800m/s，220m/s只有前者的2.8%，机腹向下机动看上去似乎没有足够大的影响。然而，在考虑过着陆点火时使用的推重比及其所需的燃料后，其实一点点速度差异都会带来极大的影响。

### 推重比

为了使火箭能够悬停，如果不考虑大气层的影响，那么它必须产生与其重量相同的推力。一个质量为1kg的物体在地球上的重量为9.8N。比如说，火箭的重量为1,000N，而在相反的方向产生1,000N的推力，就意味着推力与重量的比例将是1:1。在这种情况下，该航天器的加速度将为零，因为火箭的推力正好抵消了地球对它的拉力。

<escape><div title="一枚以1:1的推重比悬停的火箭。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_21_34_14.Still009-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">一枚以1:1的推重比悬停的火箭。（作者：每日宇航员）</div></escape>

当火箭产生了900N的推力而重量为1000N时，推重比会降至0.9:1。只要保持这个推重比，由于向下的加速度的存在，其向下的速度会增加。然而，如果火箭恢复到1:1的推重比，它并不会立刻悬停，而是保持住目前的速度，同时以目前的速度不断下降，只是加速度减少到0。

<escape><div title="一枚以1:1的推重比向下运动的火箭。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_15_33_15.Still007-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">一枚以1:1的推重比向下运动的火箭。（作者：每日宇航员）</div></escape>

#### 回到悬停

为了回到悬停状态，火箭必须将其推重比增加到1:1以上，以抵消向下的速度。比如，火箭可以把推力增加到1,100N，一旦达到零速度，就恢复到1,000N的推力。

相反的方向也是适用的。假设没有大气层，如果悬停的火箭将其推重比增加到1.5:1，它将向上加速。为了回到悬停状态，火箭必须产生低于1:1的推重比，直到其速度再次为零，这时它可以回到1:1的推重比，以维持零速度。

#### 着陆节流

在着陆过程中，推重比是发动机进行节流的一个主要因素。以猎鹰9号为例，在其最小节流设置下，仅仅启动一台发动机的推力都太大而无法悬停。为了使猎鹰9号正常着陆，其将在70%的节流以及与之适合的高度下，开始着陆点火，这样其就有余量来进行对节流程度的调整。同时在箭载计算机和其他各种仪器的工作下，理想状态下，猎鹰9号就可以在0高度到达0速度，完成一次“悬停式撞击”（hoverslam）。

#### 使用汽车的刹车模拟节流

同样，汽车的刹车过程也可以看作是一种类似着陆节流的变加速过程。你可以假设停车标志是地面，而汽车是下落的火箭。一辆汽车以50km/h的速度接近停车标志，而我们的目标是在不碰触油门并且不松开刹车的情况下将车停在停车标志前。

全力踩下刹车就相当于火箭在100%的节流设置下重新点燃发动机，而不用力踩下刹车则是最小的节流设置。对油门施力就相当于根本没有重新点燃发动机。

<escape><div title="持续地刹车直到恰好停在停车标志位置前的地面上。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/car_stop_landing.gif" height="100%" width="100%"></div></escape>
<escape><div align="middle">持续地刹车直到恰好停在停车标志位置前的地面上。（作者：每日宇航员）</div></escape>

由于内燃汽车的发动机制动，或者混合动力汽车和电动汽车的再生制动，松开油门就像点燃火箭的发动机进行减速。比如特斯拉就可以选择再生制动的量，这类似于火箭发动机的不同油门设置。

#### 使用汽车的油门模拟节流

较少的再生制动等于最低的节流设置，而较多的再生制动等于高节流设置。为了保持在同一位置停下，如果使用较少的再生制动，就需较早松开油门，而较多的再生制动就需较晚松开油门。

<escape><div title="由于较多的再生制动，车停在了离停车标志较远的位置。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/car_stop_fall.gif" height="100%" width="100%"></div></escape>
<escape><div align="middle">由于较多的再生制动，车停在了离停车标志较远的位置。（作者：每日宇航员）</div></escape>

对刹车施加不同的力，类似于对火箭发动机进行节流。如果一辆汽车提前开始刹车，那么只需要较少的刹车力。然而，如果汽车停在了停车标志前，那就相当于火箭在地面上达到零速度，并在剩下的高度中自由落体（如果发动机在此时关机的话）。

<escape><div title="调整刹车力度，并恰好停在停车标志前的地面上。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/car_stop_throttling.gif" height="100%" width="100%"></div></escape>
<escape><div align="middle">调整刹车力度，并恰好停在停车标志前的地面上。（作者：每日宇航员）</div></escape>

在此之后我们再来看看着陆过程中的重力损失。

### 着陆过程中的重力损失

重力损失发生在火箭用发动机对抗重力的时候。比如，火箭开始时的推重比为1:1。此时，每秒钟发动机产生的推力都与火箭的重量相同，没有推进剂被用来做功（机械功）。

为了使火箭减速，推重比需要高于1:1。在推重比为1.1:1的情况下，会有91%的推进剂是用来对抗重力的，而另外9%是用来做功。

如果推重比为1.5:1，那么2/3的推进剂会用于对抗重力，而1/3的推进剂用来做功。这样，与推重比为1.1:1的火箭相比，火箭的推力增加了36%，而加速度提高了400%，之前的加速度为0.1G，现在的加速度为0.5G。

<escape><div title="着陆点火中，效率，静加速度与推重比的关系图。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_24_09_06.Still001-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">着陆点火中，效率，静加速度与推重比的关系图。（作者：每日宇航员）</div></escape>

#### 越来越高

如果推重比增加到2:1，那么50%的推进剂会用于对抗重力，另50%用于做功。在这种情况下，推力增加了33%，但与推重比为1.5:1的情况相比，火箭产生的加速度提高了100%。

如果推重比增加到3:1，那么1/3的推进剂会用于对抗重力，而另外2/3的推进剂则用于做功。推力增加了50%，而火箭的加速度增加了50%。

无论推重比增加到多少，除非没有重力，否则总会有推进剂因对抗重力而损失。

以猎鹰9号及其着陆点火为例，在推重比仅为1.1:1的情况下，它将不得不在更高的高度开始着陆点火，因为加速度只有0.1G。这将导致大量推进剂的浪费，因为发动机必须得运行更长的时间。

假设，猎鹰9号的推重比为2:1，此时加速度为1G，这样就可以在离地面更近的地方开始着陆点火，并且会浪费更少的推进剂，因为发动机不会运行那么久。

（译者注：当然重力损失也可以按照冲量来理解。）

### 不同高度下Starship的翻转

Starship如此靠近地面翻转的第一个原因是为了尽可能地减少终端速度，这是因为根据终端速度公式，高度越低，空气密度越高，终端速度越低。因此，这将减少发动机为使Starship软着陆而必须做的减速工作。

安装在Starship底部裙板内的三个猛禽发动机，每一个都可以在最大推力的40%到100%之间进行节流。这样，就存在一些发动机点火组合，通过不同的节流比例，实现相同的总推力。单台发动机可以产生880kN到2200kN的推力，两台发动机可以产生1760kN到4400kN的推力，三台发动机可以产生2640kN到6600kN的推力。

<escape><div title="Starship上不同数量的猛禽发动机的总推力。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_28_13_00.Still012-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">Starship上不同数量的猛禽发动机的总推力。（作者：每日宇航员）</div></escape>

如果三台发动机以40%的最小节流运行，推重比约为2:1。这比一台猛禽的全推力要多，而且会导致很晚才能开始着陆点火，因为维持三台发动机开机的话，推重比就无法降到1:1，早点火就会导致火箭在垂直速度被消除到0后开始上升。

如果Starship失去了三台发动机中的一个，剩下的两台发动机可以节流，以匹配原有三台发动机的推力输出。而在只点火一台发动机的情况下，就可以更早地开始着陆点火，然而，其所能达到的最大推重比将只有1.6:1。与点燃三台以及两台发动机相比，这样做需要更多的推进剂。同时从应急的角度来看，如果运行中的一台发动机发生故障，将没有足够的时间重新点燃另一台发动机。

（译者注：这是本文的核心观点，即在着陆点火中，保持单台发动机点火下降是没有冗余备份能力的，因为没有时间去启动另一台发动机。译者认为此处有待商榷，需要研究较高高度下落时能为其他发动机点火争取多少时间，以及在发动机意外关机失去动力时，垂直状态下的Starship姿态能否保持稳定。）

#### 不同的翻转高度选择

Starship对于翻转机动的起始高度有各种不同的选择。最早可在2.5km的高度上进行翻转机动，同时在翻转过程中使用两台发动机，然后关闭一台，并将另一台保持在几乎最低的节流设置。

（译者注：这个最大高度显然是用推重比不能低于1，不增加着陆质量，单次点火这些条件限制下得出的，或者说在整个过程中，虽然拥有悬停能力，但并没有进行悬停，而是持续下降，与新谢坡德不同。当然可以理解，这样的理想条件更方便计算燃料的消耗。）

Starship进行翻转机动的最低高度是0.3km，这需要所有三台猛禽发动机处于最大推力。在这个高度上，Starship以及其乘员会在着陆机动中经受4.5个G的过载力。

Starship也可以在2.5km和0.3km之间的任何高度翻转。在0.55km的高度，Starship可以关闭不同数量的发动机，同时不会有漫长而低效的着陆点火。

在2.5km的高空翻转，会比在0.55km多370m/s的dv（速度增量），这些dv会直接减少运力。这是因为Starship是末级，着陆所需的370m/s的推进剂会直接占用入轨有效载荷的质量。

<escape><div title="Starship进行翻转的各种高度和相关的dv要求。（作者：德克兰·墨菲和每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_31_14_17.Still013-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">Starship进行翻转的各种高度和相关的dv要求。（作者：德克兰·墨菲和每日宇航员）</div></escape>

（译者注：取初质量m₁ = 140t，排气速度vₑ = 3200m/s，使用火箭方程，可根据不同dv计算消耗的推进剂质量，其中，2.5km高度消耗约24.7t推进剂，0.55km高度消耗约10.5t推进剂，0.3km高度消耗约6.0t推进剂，2.5km高度比0.55km高度多消耗约14.2t推进剂）

### 翻转过程中的乘员状态

尽管SpaceX的最终计划是将人送上火星，但是完成这一任务所需的着陆机动还没有成功。目前，猛禽发动机仍处于早期开发阶段，还有很多测试要进行。随着发动机可靠性的提高，着陆机动的可靠性也将提高。Starship在载人飞行之前，必须成功地完成众多的测试。

#### 会受到多少过载力

在翻转机动过程中的峰值过载只有2.5G，即地球重力的2.5倍。在从水平方向翻转到垂直方向的过程中，乘客可能会感到一些眩晕，但施加在他们身体上的压力不会高于大多数过山车上的体验。SpaceX未来可能会安装旋转座椅，这样可以把身体上经受的过载力只保持在一个方向。

<escape><div title="根据Starship SN10的飞行数据绘制的加速度图（过载力）。（作者：德克兰·墨菲和每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_38_05_17.Still015-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">根据Starship SN10的飞行数据绘制的加速度图（过载力）。（作者：德克兰·墨菲和每日宇航员）</div></escape>

事实上，尽管机尾从水平向垂直方向的摆动幅度相当大，但是Starship的机头并没有那么大的移动量。同时，与Starship相比，猎鹰9号在着陆时的过载力可以达到5个G。

<escape><div title="Starship机头与机尾的相对运动。（作者：每日宇航员）" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/starships-belly-flop-maneuver-zh-hans/Belly-Flop-MAIN-Reshoot.00_38_33_25.Still016-1024x576.webp" height="80%" width="80%"></div></escape>
<escape><div align="middle">Starship机头与机尾的相对运动。（作者：每日宇航员）</div></escape>

### 总结

Starship正在进行一种新的，独特的着陆机动。从来没有其他公司尝试过如此复杂的火箭回收方法。为了找到最佳的翻转高度，要考虑到终端速度，重力拖拽/重力损失的影响，以平衡效率和安全。

SpaceX的结论是，开始Starship翻转机动的最佳高度是0.55km左右。在这个高度，Starship需要花掉的dv为250m/s，同时也有能力在发动机故障的情况下安全降落，被认为是最有效率的。同时这将使Starship使用1.6:1的最佳推重比来点燃发动机以进行减速和降落。

Starship可以放入轨道的有效载荷的质量也可以由它执行翻转机动的高度决定。着陆时使用的dv越少，意味着可以使用更多dv将物体或人类放入轨道。毕竟，SpaceX的总体目标是利用Starship最终将人类送上月球，火星和其他地方。

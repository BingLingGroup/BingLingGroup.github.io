---
layout:     post
title:      github pull request流程演示
date:       2019-02-01 09:00:00
author:     "冰灵"
categories:
    - 演示
tags:
    - 教程
    - sourcetree
    - git
    - github
    - pull request
    - windows
thumbnail: "https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/github%20pull%20request%E6%B5%81%E7%A8%8B%E6%BC%94%E7%A4%BA/[Crappy%201080P]%20Code%20Lyoko%20S4E72_20180219_191113.614.png"
---
>[题图来源\(Code Lyoko E72的07分17秒位置\)][E720717]将浏览器拉窄即可看到全图。
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。

<escape><font size=4>目录</font></escape>

1. [简介](#简介)
2. [程序准备](#程序准备)
   - 2.1 [安装sourcetree](#安装sourcetree)
   - 2.2 [安装git](#安装git)
3. [pull request流程](#pull-request流程)
   - 3.1 [远程克隆(fork)他人仓库](#远程克隆-fork-他人仓库)
   - 3.2 [克隆(clone)你刚创建的副本并修改本地文件](#克隆-clone-你刚创建的副本并修改本地文件)
   - 3.3 [提交(commit)你刚才进行的改动](#提交-commit-你刚才进行的改动)
   - 3.4 [推送(push)你刚才的提交(commit)](#推送-push-你刚才的提交-commit)
   - 3.5 [我想反悔推送(push)怎么办](#我想反悔推送-push-怎么办)

本教程面向会使用谷歌的github零基础使用者，同时也作为刚入门github pull request的笔者的简单记录。

<escape><div title="就是搜不到这种操作.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/github%20pull%20request%E6%B5%81%E7%A8%8B%E6%BC%94%E7%A4%BA/你不会搜索吗.jpg" height="60%" width="60%"></div></escape>
<escape><div align="middle">就是搜不到这种操作.jpg</div></escape>

### 简介

pull request是什么？[Pull Request 的命令行管理 - 阮一峰的网络日志][what_is_pr]
>"Pull Request 是一种通知机制。你修改了他人的代码，将你的修改通知原来的作者，希望他合并你的修改，这就是 Pull Request。"

直接翻译过来可以理解为拉取(pull)请求(request)。推送(push)和拉取(pull)是github多种基本操作之一，推送一般指将本地git仓库的特定分支(branch)推送到远程仓库(譬如github的某个repository)的特定分支(也称remote branch)，pull则是相反的操作。之所以称作是拉取请求，我个人的理解是你对别人的仓库里一个分支的文件进行了改动，向别人发起请求来拉取你一个分支里的改动，只不过这里的拉取是远程到远程的操作，都是github上的仓库而和本地没有关系。

### 程序准备

以下安装准备针对的操作系统环境是windows 10，git图形界面则是sourcetree，部分sourcetree不能解决的问题会涉及到git Bash操作。

[返回pull request流程](#pull-request流程)

#### 安装sourcetree

[sourcetree][srctree]是一个并不那么省心的git图形界面软件，但是git图形界面软件就那么几个，只能将就着用了，不然就命令行吧。

安装时建议使用内嵌(Embedded)版git，内嵌版git在添加多个github账号时使用起来较为繁琐，但是sourcetree使用外部git时*好像*(此处存疑)无法使用oauth一键绑定github账号，也要注意全局git config(位置一般在/Users/你的用户名/.gitconfig)中的用户设置，总之我印象里面是有bug。相比之下单独使用git配置多账户的教程可以参考[同一客户端下使用多个git账号 - 简书][multi_git]。如果要使用系统自带的git，请自行安装git。~~其他问题包括如何使用sourcetree，如何在sourcetree中登录github账号等，就自己谷歌吧，这里略去~~

#### 安装git

安装git之前我建议先安装一个windows的第三方包管理器[chocolatey][choco_install_site]，因为chocolatey可以自动帮你维护环境变量-系统变量，同时还能帮你更新软件，使用起来更加安心。chocolatey的使用范例可以参考[使用 ffmpeg 拼接 bilibili 客户端所下载的分段 flv 视频][choco_eg]。

安装好chocolatey之后，用管理员权限运行命令行或者Powershell(譬如Win+X调出快捷键菜单运行)，输入以下指令来安装git。

```bash
choco install git -y
```

### pull request流程

pull request需要的流程主要是先远程克隆([fork][fork_zhihu])他人的仓库，然后克隆(clone)到本地，接着在本地，对文件进行修改(modify)，修改之后，提交(commit)并推送(push)到你远程的分支(branch)上。再打开别人的项目主页，点击中间的New pull request建立新的拉取请求，可以看到一个对比页面，选择好了之后填写说明创建(Create pull request)即可。具体参考[Pull Request 的命令行管理 - 阮一峰的网络日志][what_is_pr]，这里不再赘述。

以下是遵循[上述环境](#程序准备)下进行操作的一部分提示。

#### 远程克隆(fork)他人仓库

打开他人的仓库(repository)主页，你会看到右上角有一个Fork按钮，点击Fork，创建他人仓库在你github账号下的副本。

#### 克隆(clone)你刚创建的副本并修改本地文件

打开sourcetree，点击Clone，克隆你刚才创建的远端仓库副本，然后在本地修改文件。

#### 提交(commit)你刚才进行的改动

这里面有两个坑，我先说明一下。

首先，注意[关闭换行符自动转换][Alert_1]，如果你使用那种一旦将CRLF转换成LF就会影响代码运行或者其他严重后果的编程语言或者集成开发环境(如Batch，Vivado verilog等)，请务必关闭这一选项。其他情况也请酌情关闭。~~LF虽好，可我大窗国自有国情在此，原不藉外夷货物以通有无~~

其次，注意你要pull request的仓库是否开启了提交验证(commit verified)。

<escape><div title="提交验证的后台设置位置，当然只有权限狗才能看得到_1.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/github%20pull%20request%E6%B5%81%E7%A8%8B%E6%BC%94%E7%A4%BA/%E6%8F%90%E4%BA%A4%E9%AA%8C%E8%AF%81-1.png" height="70%" width="70%"></div></escape>

<escape><div title="提交验证的后台设置位置，当然只有权限狗才能看得到_2.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/github%20pull%20request%E6%B5%81%E7%A8%8B%E6%BC%94%E7%A4%BA/%E6%8F%90%E4%BA%A4%E9%AA%8C%E8%AF%81-2.png" height="50%" width="50%"></div></escape>

~~不是这两张~~，应该是下面这些。

譬如仓库的readme里面或者contribute文档里面明确说明pull request需要签名验证~~此处懒得找图了~~。

打开某个pull request后看到有人因为没有提交验证~~而格格不入~~。

<escape><div title="没有提交验证而格格不入.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/github%20pull%20request%E6%B5%81%E7%A8%8B%E6%BC%94%E7%A4%BA/%E6%8F%90%E4%BA%A4%E9%AA%8C%E8%AF%81-3.png" height="80%" width="80%"></div></escape>

或者打开提交历史(在仓库主页点击commits即可看到)，最近的提交都有签名。

<escape><div title="一列漂亮的小绿标.jpg" align="middle"><img src="https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/github%20pull%20request%E6%B5%81%E7%A8%8B%E6%BC%94%E7%A4%BA/%E6%8F%90%E4%BA%A4%E9%AA%8C%E8%AF%81-4.png" height="80%" width="80%"></div></escape>

关于<escape><a name = "签名验证"><a href="#签名验证">签名验证</a></a></escape>的具体操作方法，可以参考我写的另一篇文章[在windows版的sourcetree上设置gpg签名](在windows版的sourcetree上设置gpg签名.html)。

如果你已经创建了pull request，忘记或者不清楚对提交进行签名，却被要求要进行签名~~被格格不入~~的时候，这时可以通过现在本地软重置提交再强制推送的方式更改掉你之前没有签名的分支，详见[反悔推送](#我想反悔推送-push-怎么办)的方法。注意你在强制推送之前，请务必先在本地做好带gpg签名的提交。

#### 推送(push)你刚才的提交(commit)

这里也有两个坑。

首先是sourcetree的问题。如果你在sourcetree里面绑定了多个github账号，提交能成功，却发现推送总是失败的时候，注意在工具-选项-验证-账户里，把当前仓库的账号设置成默认账号即可解决问题，原因是sourcetree对多个github账号的oauth验证管理有缺陷，似乎不能针对单个仓库进行账户密码管理。或者你也可以请[自行配置][sourcetree_ssh]ssh而不使用sourcetree的oauth验证，这样其实就和命令行git的配置使用差不多了。~~这样的话真的感觉sourcetree有个GUI用~~

其次是如果有人有整洁强迫症，可以考虑在推送时推送到一个单独的分支上，而不是推送到副本分支上，譬如你可以单独新建一个patch-xxx这样的分支等等，具体请谷歌。反正合并的时候自己知道用哪个分支合并就可以了，命名规范主要是记录起来好看一点。

#### 我想反悔推送(push)怎么办

假如你推送了一个错误的东西上去，再纠正还得再推一个，感觉没必要的时候，可以使用这个方法。

在sourcetree里，点击你要重置回去的那一次提交，右键-重置当前分支到此次提交-软合并(保留所有本地改动)，确定你做的修改没问题后，再正常地在本地提交一次，提交完了之后，确定本地仓库没问题的时候，右上角点击命令行模式，打开git bash，输入以下指令即可。参考[git撤销&回滚操作 - 李刚的学习专栏 - CSDN博客][git_revert_intro]。

注意尽量只在自己的仓库上进行强制推送，强制推送过于暴力，可能会造成一些不可挽回的后果。

```bash
git push -f
```

返回<escape><a href="#签名验证">签名验证</a></escape>

[E720717]: https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/github%20pull%20request%E6%B5%81%E7%A8%8B%E6%BC%94%E7%A4%BA/b07fd0f8ly1fyvvhry8scj21hc0u0hcw.jpg
[what_is_pr]: http://www.ruanyifeng.com/blog/2017/07/pull_request.html
[srctree]: https://www.sourcetreeapp.com/
[multi_git]: https://www.jianshu.com/p/89cb26e5c3e8
[choco_install_site]: https://chocolatey.org/docs/installation
[choco_eg]: https://blessing.studio/use-ffmpeg-to-concat-flv-videos-downloaded-by-bilibili-client/
[fork_zhihu]: https://www.zhihu.com/question/20431718
[Alert_1]: https://github.com/cssmagic/blog/issues/22
[sourcetree_ssh]: https://blog.csdn.net/tengdazhang770960436/article/details/54171911
[git_revert_intro]: https://blog.csdn.net/ligang2585116/article/details/71094887
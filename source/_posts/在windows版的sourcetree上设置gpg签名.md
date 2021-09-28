---
layout:     post
title:      在windows版的sourcetree上设置gpg签名
date:       2019-02-01 14:00:00
author:     "冰灵"
categories:
    - 演示
tags:
    - 教程
    - sourcetree
    - git
    - github
    - gpg
    - windows
thumbnail: "https://raw.githubusercontent.com/BingLingGroup/BingLingGroup.github.io/img/%E5%9C%A8windows%E7%89%88%E7%9A%84sourcetree%E4%B8%8A%E8%AE%BE%E7%BD%AEgpg%E7%AD%BE%E5%90%8D/[Crappy%201080P]%20Code%20Lyoko%20S4E73_001150.399.png"
---
>[题图来源\(Code Lyoko E73的11分50秒位置\)][E731150]将浏览器拉窄即可看到全图。
>PC版网页左上角从上到下第二个图标是目录，请多用目录。
>网页右下角按钮为返回顶部，请多用返回顶部来查看顶部目录。

<escape><font size=4>目录</font></escape>

1. [简介](#简介)
2. [原理](#原理)
3. [程序准备](#程序准备)
   - 3.1 [安装Gpg4win](#安装Gpg4win)
   - 3.2 [安装sourcetree](#安装sourcetree)
4. [设置Gpg4win](#设置Gpg4win)
5. [设置github](#设置github)
6. [设置sourcetree](#设置sourcetree)
7. [疑难解答](#疑难解答)

本文章主要讲解在使用windows版sourcetree对github commit进行签名操作，本方法主要优点在于可根据不同仓库设置是否使用何种签名，而非全局使用某一特定签名。

### 简介

GPG签名是什么？[怎样为你的 Commit 加上 GPG 的签名][longtian-gpg-howto]
>为 Commit 带上 GPG 的签名就是一个很好的开始，它能够在一定程度上保证安全性。

简而言之就是类似账号两步验证之类的确保你的github账号创建的提交(commit)是你本人做出的而不是别人盗用你账号做出的，类似的方法有mega网盘的账户还原密钥。

### 原理

[GPG入门教程 - 阮一峰的网络日志][gpg_intro]

### 程序准备

以下程序准备针对的操作系统环境是windows 10，git图形界面则是sourcetree。

#### 安装Gpg4win

[Gpg4win - Secure email and file encryption with GnuPG for Windows](gpg4win_site)

#### 安装sourcetree

[sourcetree][srctree]
一些设置建议可以参考[github pull request流程演示之安装sourcetree](github pull request流程演示.html#安装sourcetree)。

### 设置Gpg4win

安装的是Gpg4win，此处以Kleopatra为例，同样你也可以使用其他GPG密钥管理界面，密钥管理方法应该是类似的。选择菜单栏-文件-新建密钥对，根据提示自行创建密钥，也可以参考[GPG入门教程 - 阮一峰的网络日志][gpg_intro]。

**注意**， 邮箱账号需为你在github账号中验证过(verified)的邮箱，来源[Generating a new GPG key - User Documentation][GPG_email]，同时第8步中github也给你了隐藏邮箱的方法。

创建完毕后，点击刚才创建的密钥对，右键-细节，公钥就是Kleopatra里面的指纹部分，点击导出获得私钥，你刚才被要求输入的那段密码是用于保护私钥的密码，并不是私钥本身。

### 设置github

参考github官方文档[Adding a new GPG key to your gitHub account - User Documentation][GPG_github]，以及官方推荐的设置步骤[About commit signature verification - User Documentation - gpg][commit_GPG_github]。

此处github需要粘贴进去的gpg key指的是在前一个步骤中生成的私钥。

### 设置sourcetree

严格意义上这里并不是设置sourcetree，而是设置每个仓库(repository)提交所需的配置文件，位置是：
>仓库文件夹/.git/config

全局(global)配置文件在windows当前用户的用户文件夹根目录下：
>C:/Users/你的用户名/.gitconfig

当然如果你用命令行操作git的话，可以参考git官方文档的local参数说明[git - git-config Documentation - local][git-config-docs]和配置文件读取顺序说明[git - git-config Documentation - files][git-config-docs-files]。

根据配置文件读取顺序说明，可以得知git提交(commit)的时候，在不加特定参数时，会先读取全局配置文件(global git config)，然后再读取本地配置文件(local git config)，如果在全局配置文件里面设置了特定用户的gpg签名，而你有多个github用户或者多个gpg签名或者有的仓库不想使用gpg签名的时候，就会出现混乱。

本篇文章原创部分最大的地方也就在这里~~换句话说其他地方都是抄的~~，之前我参照的一个教程[在Windows版的Sourcetree上启用GPG签名][windows-srctree-gpg-enabled]只说了全局的方法，但是如上所述会出现混乱的情况，所以我这里给出的方法是不在全局配置文件处进行设置。而是对每个仓库的配置文件进行设置，设置方法和全局配置文件的写法一样，添加以下字段即可。

```JSON
[user]
    name =
# name指gpg签名生成时你填的名字
    email =
# email指gpg签名生成时你填的邮箱
    signingkey =
# signingkey指公钥ID的后八位，或者说指纹的后八位
[commit]
    gpgSign = true
# 此处gpgSign的值可为true或者false，true指开启gpg签名
[gpg]
    program = c:\\Program Files (x86)\\GnuPG\\bin\\gpg.exe
# 这里program的位置是Gpg4win安装时的默认位置
# 如果你当时没装在这个路径，请自行修改
# 注意两条反斜线中一条是用来转义的，务必确保路径名中的反斜线是有两条的
```

这样设置好了以后，再提交的时候，git就会调用gpg，要求你对提交进行签名，此时你需要输入那串用于保护私钥的密码。

### 疑难解答

前面所讲都是让sourcetree使用内嵌的git的情况下进行的操作，因为sourcetree使用oauth绑定多个github账号时的[各种问题](github pull request流程演示.html#推送-push-你刚才的提交-commit)，所以没怎么试过用外部git单独操作的情况是否能成功设置。理论上这套教程也可以用于单独安装的git，~~毕竟以上各种玄学问题的解释都是从git的官方文档里找的~~，我本人尝试的结果是可以用于强制推送的指令，其他还没试过。

[E731150]: https://ws1.sinaimg.cn/large/b07fd0f8ly1fzqx5qjwv4j21hc0u0b29.jpg
[longtian-gpg-howto]: https://github.com/longtian/gpg-howto
[gpg_intro]: http://www.ruanyifeng.com/blog/2013/07/gpg.html
[gpg4win_site]: https://www.gpg4win.org/
[srctree]: https://www.sourcetreeapp.com/
[GPG_email]: https://help.github.com/articles/generating-a-new-gpg-key/#generating-a-gpg-key
[GPG_github]: https://help.github.com/articles/adding-a-new-gpg-key-to-your-github-account/
[commit_GPG_github]: https://help.github.com/articles/about-commit-signature-verification/#gpg-commit-signature-verification
[git-config-docs]: https://git-scm.com/docs/git-config#git-config---local
[git-config-docs-files]: https://git-scm.com/docs/git-config#FILES
[windows-srctree-gpg-enabled]: https://xiaoxi654.me/2018/12/28/%E5%A6%82%E4%BD%95%E5%9C%A8Windows%E7%89%88%E7%9A%84Sourcetree%E4%B8%8A%E5%90%AF%E7%94%A8GPG%E7%AD%BE%E5%90%8D/
title: Web编程之旅（一）
date: 2014-11-26 11:35:46
categories:
- Web编程之旅
tags:
- web编程
- UI
---

## 前言

昨天晚上快11点的时候收到了一个学妹的邮件，问我关于web编程方面的问题，她说她很迷茫，不知道如何开始学习Web编程，希望我能推荐一些入门的书籍给她。看到这封邮件我也犯难了，因为我确实不知道现在关于JS、CSS和HTML方面的入门书哪些比较好，所以才有了写这样一篇博客的想法，希望能帮助还在大学或者对web编程感兴趣的人一些帮助。

## 准备

从我个人的经验来说刚刚开始学习编程之前有一个好的知识组织和代码管理是非常有必要的，在学习的过程中我们会经常忘记之前我们已经练习过的那些知识点，如果没有一个好的知识组织管理在学习的过程中我们会步履蹒跚，每次碰到这类问题都会从头开始再学习一遍，这个一次两次还好说时间久了真的会很让人沮丧的。
幸运的是我们现在生活在云时代，网络上有各种各样的免费工具空间可供我们选择，如果你完全是一个编程的门外汉的话，那么请按照我下面所说的步骤来建立自己的知识管理吧。
<!-- more -->
- [GitHub](https://github.com/) - 你的代码仓库。
- [Evernote](https://www.yinxiang.com/) - 你的个人云笔记。
- [Codepen](http://codepen.io/) - 作为Web程序员这里可能是最好的练习和偷师的地方，我自己经常上去偷师。
- [Hexo](http://hexo.io/) - 可选项，如果可能的话写点自己的博客吧，这篇博客就是站在hexo和github的肩旁上。

> 这里codepen的账号是不需要注册的，直接可以用github的账号登录，当然以后你会发现github的账号可以登录很多程序员的世界，嘿嘿。
  
> 关于如何注册github的账号请自行google一下吧。

## 给自己一个目标

很多时候我们不知道如何学习的一个最大矛盾是我们不知道我们学习之后能干什么，没有目标的学习这个是很痛苦的，很容易迷茫，我个人的经验是学习是为了玩，所以让我们先弄个**“个人主页”**玩玩吧。

## 准备开发环境

虽然我是个linux党而且非常讨厌在windows下编程（没有一个强大的shell对命令党而言是致命的），但是考虑到linux上的编程对还没入门的学弟学妹们起点有点小高，所以这篇文章还是决定回到windows上，还好对于web开发而言windows和linux在初级开发上差别不是很大。有条件的同学我还是强烈推荐自己装个虚拟机在linux上体验开发吧，这对以后的提高是很有帮助的。


### 编辑器
Web开发对编辑器的要求其实不高，因为web编程不需要编译程序，完全可以无视IDE（集成开发环境）。
Sublime Text编辑器最近几年在程序员中超级火，全平台支持，丰富的插件，皮肤也很棒，连我这个VIM死党在离开linux时候都会不由自主的使用它（windows下的gvim真的不好用），所以我们我们就选择他作为我们的主力开发编辑器好了，你可以从[这里](http://www.sublimetext.com/3)下载它。

1. 刚刚下载的sublime text 是没有包管理器的所以我们还需要做为它安装上包管理器,[这里](https://sublime.wbond.net/installation)会教你怎么安装包管理器。
2. 安装完包管理器以后我们先为我们的web开发安装一些必要的插件。
  - __HTML5__支持 - 打开Sublime Text编辑器按__Ctrl+Shift+P__（国内的网络可能会打开比较慢，如果实在无法打开的话可以去[这里](https://sublime.wbond.net/)手动下载安装），输入“__install package__” 然后按回车，等待新的弹出框出来，然后在弹出框里面输入“__HTML5__” 然后按回车，这样就安装了HTML5扩展支持了。
  - __Javascript__支持 - 同安装HTML5支持一样先按“__Ctrl+Shift+P__”然后输入“__install package__”，最后输入“__Javascript Beautify__”，按回车安装。
  - __CSS__支持 - 同上知识最后输入的时候输入CSS就行了了，关于CSS的插件我用的不多，同学们按自己的需要安装。

### 安装Web服务器

#### 安装Nodejs

Nodejs是个好东西啊，有了它Javascript几乎可以做其他语言能做的一切事情，同时其他程序不能做的事情Javascript也能做，没有比这个更美妙的了。

首先去[官网](http://nodejs.org/)下载它的安装包。
> 由于windows没有很强的shell，所以我这里使用了cmder作为windows下的shell。老样子去[官网](http://bliker.github.io/cmder/)下载，这里请注意下载它的完全版本也就是250MB的那个版本，这个完全版本包含了很多linux shell的命令，这个让人无比的舒爽啊。

#### 安装static-server

打开命令行窗口输入
```sh
npm install static-server -g
```
> 如果安装包错或者失败的话请使用管理员权限运行cmder。

好了以上就是你所需要搭建的开发环境的全部是不是很简单


### 第一个程序Hello World！

1. 打开命令行框口,创建第一个工程

![cmd](https://raw.githubusercontent.com/hxshandle/image-pool/master/web%E7%BC%96%E7%A8%8B%E4%B9%8B%E6%97%85/hello-world.gif)

2. 创建index.html文件

![create](https://raw.githubusercontent.com/hxshandle/image-pool/master/web%E7%BC%96%E7%A8%8B%E4%B9%8B%E6%97%85/create-index-html.png)

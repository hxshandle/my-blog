title: github atom编辑器
date: 2014-11-30 18:46:16
categories:
- 杂七杂八
tags:
- 编辑器

---

## Github给程序员的新编辑器

其实我很2年前就听说过Atom编辑器，也确实网上看过一些介绍，但是当第一眼看到它的样子的时候我惊呆了，这个不是Sublime Text嘛？Github这是闹哪样啊，重复造轮子啊，随即Atom就被我自动过滤了。时隔2年以后，终于鼓起勇气弄下来玩了一把，总的来说感觉还凑合。

<!-- more -->

## 使用感受

1. 如果你是一个Sublime Text的用户那么从Sublime Text转移到Atom几乎没有任何困难，你一样可以用**Ctrl+Shift+P**,**Ctrl+P**。
2. Atom不用像Sublime Text那样需要另外安装包管理器，直接就内置了，这个感觉还是比较好的。![设置](https://raw.githubusercontent.com/hxshandle/image-pool/master/blog/1.PNG)
3. 文字菜单栏这回终于可以完全隐藏了，这对于用惯了VIM的我来说那个菜单条真的很影响心情。
4. __Ctrl+\__可以显示和隐藏左侧的菜单栏![设置](https://raw.githubusercontent.com/hxshandle/image-pool/master/blog/2.PNG)
5. 如果你编辑的工程是git目录的话，左侧的文件导航能够很方便的看到哪些文件有变动，哪些文件是在.gitignore里面的，这点我觉得还是很不错的。

## 问题
1. 安装Emmet插件的时候始终无法成功安装提示nodejs的npm报错，一开始以为只是windows平台上的问题，换上mac发现问题依旧，网上的方法也都试了一遍，无解，Atom beta果然还是不够稳定啊。
2. Soft wrap这个功能很奇怪，每次自动换行的位置都不相同，完全找不到规律，编辑文本的时候感觉会很乱。
3. 鼠标选区的时候总感觉有延迟，这个可能是浏览器实现的问题，毕竟这个Atom是基于web技术的浏览器，其实你可以认为它就是一个独立的web application。

以上这些暂时就是Atom使用一天的使用感受

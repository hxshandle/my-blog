title: 使用Google Drive作为Blog的图床
date: 2014-12-11 12:41:46
categories:
- 杂七杂八
tags:
- 其他

---

有时候会碰到需要在blog或者codepen.io写一些东西的时候需要用到图片，如果使用github来上传图片的话虽然也可以，但是总感觉贬低了github，使用起来也不是很方便，所以想到了使用Google Drive作为图床使用。

登陆Google Drive上传图片之后点击获取链接，我们会得到一个如下的URL地址
```
https://drive.google.com/open?id=YOUR_FILE_ID&authuser=0
```
但是这个地址是无法直接作为image的src值的，我们需要稍微做一点修改(你必须设置一下google的共享属性**知道此链接的任何人都可以查看**)
```
https://drive.google.com/uc?export=view&id=YOUR_FILE_ID
```
如果需要让这个文件直接支持下载的话，请使用如下地址
```
https://drive.google.com/uc?export=download&id=YOUR_FILE_ID
```


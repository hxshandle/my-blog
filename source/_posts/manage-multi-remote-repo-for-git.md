title: git管理多个远程仓库
date: 2015-02-25 11:16:22
categories:
- git
tags:
- git
---

今天试用了一下BAE，结果在创建完应用的时候居然自己给我分配了一个新的BAE的git repo地址，我人当时就傻眼了，我已经有github和git@OSC了，难道现在还要再多一个百度的git仓库,整个人当时就不好了。还好伟大的git有各种玩法。

首先在原有的git项目上添加百度的git地址,注意其中bae是新的remote branch的别名。
```
git remote add bae https://git.duapp.com/appidxxxxxxx
git remote -v
```

添加完百度的远程仓库以后第一步是要pull他，否则你无法提交仓库代码
```
git pull bae
```
执行到这里如果你是nodejs项目的话package.json一定会冲突，处理完冲突以后按照常规方法执行提交合并

```
git add .
git commit -am "your comment"
```

好了执行到这里我们对本地仓库的改动就全部完成了下面是推送，这里我们需要推送2次

```
git push origin master 
git push bae master
```
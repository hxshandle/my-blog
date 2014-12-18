title: 让mac可以运行任何来源的程序
date: 2014-12-18 11:06:20
categories:
- 杂七杂八
tags:
- 其他
---

今天想在公司的MAC电脑上装一个破解版的Sketch3，你知道的最为一个屌丝600多大洋买一个软件我还是很舍不得的。可是蛋疼的事情发生了，软件下完了发现不能用，原因是安全策略不允许我运行非app store和认证的程序，并且由于公司的安全策略这个选项是灰色的无法修改，我了个去啊，这个怎么可以了。所以经过1/4柱香的google找到的解决办法，So easy，一个命令就解决了
```sh
$ sudo spctl --master-disable
```
如果要还原的话也是一句命令就ok了
```sh
$ sudo spctl --master-enable
 ```
 命令执行前
 ![命令执行前](https://drive.google.com/uc?export=view&id=0B7MTssZ3kd9laVV5QVZndVRhNWM)
 命令执行后
 ![命令执行后](https://drive.google.com/uc?export=view&id=0B7MTssZ3kd9lbU9zcHlyWlJPbWM)

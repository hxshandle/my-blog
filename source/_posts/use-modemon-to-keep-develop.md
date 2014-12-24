title: 使用nodemon让Express server自动重启
date: 2014-12-24 20:12:20
categories:
- nodejs
tags:
- nodejs
- Express
---

在使用Express做快速web开发的时候，当程序文件一变动就需要重启server这个对于一个高效的web程序员来说是非常糟糕的体验，今天发现了一个不错的工具[nodemon](http://nodemon.io/)，当文件变动以后它可以自动重启Express服务器，当然重启Express服务器只是一个很小的功能，它可以做更多的事情，具体的可以访问它的文档。

安装

```shell
$ npm install -g nodemon
```

使用

```shell
$ cd to_your_express_project_root_path
$ nodemon bin/www
```

在默认情况下nodemon只会监控当前操作目录，当然你也可以通过配置来增加，这里就不多做介绍了。


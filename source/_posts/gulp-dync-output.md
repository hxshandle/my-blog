title: Gulp动态监控目录并且格式化输出
date: 2015-03-31 20:46:03

categories:
- nodejs
tags:
- nodejs
- gulp

---

如果一个web项目是由许多小的子项目（或者称之为组件）组合起来的，同时每个子项目都有属于自己的js，scss文件，但是当编译的时候（或者开发时）我们需要将子项目的这些资源文件移动到web项目的public目录下面，我们肯定不希望每次都手动copy这些文件，那样实在是太没有效率了。
让我们看一下如下目录结构
```
project-root
+---biz-module
|   +---404
|   +---auth
|   +---home
|   +---login
|   |   \---template
|   |       \---scss
|   \---user
+---public
|   +---css
|   |   \---login
|   \---modules
|       \---Material
|           +---css
|           +---fonts
|           \---js
\---template
```

<!-- more -->
在这个工程结构中每个组件模块以目录的封装形式放在biz-module目录下面，这些组件里面包含了自己所有的静态资源，但是对于web项目来说我们通常会把所有的静态资源放到public目录下面。如果手工复制这些资源文件明显不可能，通过配置文件，如果项目足够大配置文件会让人发疯的。幸运的是我们有gulp这个强大的构建工具，让我们可以用程序员的方式来自动构建。

当biz-module目录下面有新添加的组件的时候我们完全不需要为其添加新的配置文件内容，而是通过目录扫描自动将其加载，并且将组件内地静态资源自动移动到项目的public目录中。

下面的示例当中我们会将所有组件中的scss代码编译到项目的public/css目录下，并且根据不同的组件名称创建子目录。这里只是抛砖引玉，你可以用这个机制来分割你的组件，并且保证各个组件之间的完全结构，让项目做到插件化。

```javascript
"use strict";
var gulp = require('gulp');
var jade = require('gulp-jade');
var sass = require('gulp-ruby-sass');
var path = require('path');
var _ = require('lodash');
var fs = require('fs');


function watchBizModuleSCSS(cfg) {
  gulp.task(cfg.name + "-compile-scss", function() {
    return sass(cfg.path)
      .on('error', function(err) {
        console.error('Error!', err.message);
      })
      .pipe(gulp.dest(cfg.dist));
  });
  gulp.task(cfg.name + '-scss', function() {
    gulp.watch('biz-module/' + cfg.name + '/**/*.scss', [cfg.name+'-compile-scss']);
  });
}

// dync watch for biz-module

var bizModules = fs.readdirSync(path.join(__dirname, 'biz-module'));
var _tasks = [];
_.each(bizModules, function(m) {
  var hasSCSS = fs.existsSync(path.join(__dirname, 'biz-module', m, 'template', 'scss'));
  if (hasSCSS) {
    var cfg = {
      name:m,
      path:'biz-module/'+m+"/template/scss/",
      dist:'public/css/'+m
    }
    watchBizModuleSCSS(cfg);
    _tasks.push(m+'-scss');
    console.log("%s---->%j",m,cfg);
  }
});

gulp.task('default', _tasks);
```
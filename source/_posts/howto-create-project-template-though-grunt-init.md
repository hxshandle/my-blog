title: 通过grunt-init模板来创建web项目
date: 2015-02-10 10:55:21
tags:
- web
- nodejs
- grunt
---

做了多年的web开发，自己也经常有各种各样的想法希望快速实现一下，这个时候第一遇到的问题就是搭建环境，虽然现在有很多HTML5的现成的模板可以使用，但毕竟自由也有很多年的积累，自己的东西用起来总是顺手许多，所以才有了使用grunt-init来搭建自己的模板的想法。

## 关于Grunt

首先现代的软件开发依赖越来越大，分工越来越细，这样也导致了项目工程中需要引入越来越多的第三方依赖，若干年前作为web项目我们还可以自己应付，但是随着web的发展项目构建也成为了web项目不得不面对的问题。在别的语言中，java有maven，python有pip，ruby有gem，那么作为前端的主力nodejs怎么自然而然的也就出现的Grunt 它就是nodejs世界的项目构建工具。

## 准备

首先我们必须要有nodejs环境，至于怎么装nodejs环境这里就不多说了，网上的一堆一堆的文章。

### 安装grunt 和grunt-init
```shell
$ npm install -g grunt
$ npm install -g grunt-cli
$ npm install -g grunt-init
```

<!-- more -->

### 创建工程

所谓的工程其实就是一个目录，随意在你的系统中创建一个空目录，文章一下所有的操作都会在这个目录下面。这里我先建立自己的基于weixin js sdk的项目模板,一个好的习惯是目录名称应该能够体现你工程的目的和属性。
```shell
$ mkdir grunt-init-weixin-jssdk
$ cd grunt-init-weixin-jssdk
```

按照grunt-init Customer template的说明创建如下内容
```shell
$ touch template.js
$ touch rename.json
$ mkdir root
```

其中root目录下的所有文件和子目录都会被复制到所创建的项目中。所有被复制的文件都将会当成模板来处理，在文件中被__{% raw %}{% %}{% endraw %}__包围的内容都将会被执行中的变量（rename.json）所替换,除非你设置了noProcess选项。

rename.json示例
在json中"src/name.js"必须存在于root目录下。在项目创建的过程中改文件名会被自动按照你所给出的模式改名。

```JSON
{
  "src/name.js": "src/jquery.{% raw %}{%= name %}{% endraw %}.js",
  "test/name_test.js": "test/{% raw %}{%= name %}{% endraw %}_test.js",
  "test/name.html": "test/{% raw %}{%= name %}{% endraw %}.html"
}
```

template.js示例
这里是我们主要编写的内容，我们需要在这里设置一系列的问题来完善项目所需要的内容

```javascript
/*
 * grunt-init-jquery
 * https://gruntjs.com/
 *
 * Copyright (c) 2013 "Cowboy" Ben Alman, contributors
 * Licensed under the MIT license.
 */

'use strict';

// Basic template description.
exports.description = 'Create a jQuery plugin, including QUnit unit tests.';

// Template-specific notes to be displayed before question prompts.
exports.notes = '_Project name_ should not contain "jquery" or "js" and ' +
  'should be a unique ID not already in use at plugins.jquery.com. _Project ' +
  'title_ should be a human-readable title, and doesn\'t need to contain ' +
  'the word "jQuery", although it may. For example, a plugin titled "Awesome ' +
  'Plugin" might have the name "awesome-plugin".' +
  '\n\n'+
  'For more information, please see the following documentation:' +
  '\n\n'+
  'Naming Your Plugin      http://plugins.jquery.com/docs/names/\n' +
  'Publishing Your Plugin  http://plugins.jquery.com/docs/publish/\n' +
  'Package Manifest        http://plugins.jquery.com/docs/package-manifest/';

// Template-specific notes to be displayed after question prompts.
exports.after = 'You should now install project dependencies with _npm ' +
  'install_. After that, you may execute project tasks with _grunt_. For ' +
  'more information about installing and configuring Grunt, please see ' +
  'the Getting Started guide:' +
  '\n\n' +
  'http://gruntjs.com/getting-started';

// Any existing file or directory matching this wildcard will cause a warning.
exports.warnOn = '*';

// The actual init template.
exports.template = function(grunt, init, done) {

  init.process({type: 'jquery'}, [
    // Prompt for these values.
    init.prompt('name'),
    init.prompt('title', function(value, data, done) {
      // Fix jQuery capitalization.
      value = value.replace(/jquery/gi, 'jQuery');
      done(null, value);
    }),
    init.prompt('description', 'The best jQuery plugin ever.'),
    init.prompt('version'),
    init.prompt('repository'),
    init.prompt('homepage'),
    init.prompt('bugs'),
    init.prompt('licenses', 'MIT'),
    init.prompt('author_name'),
    init.prompt('author_email'),
    init.prompt('author_url'),
    init.prompt('jquery_version')
  ], function(err, props) {
    // A few additional properties.
    props.jqueryjson = props.name + '.jquery.json';
    props.dependencies = {jquery: props.jquery_version || '>= 1'};

    props.keywords = [];

    // Files to copy (and process).
    var files = init.filesToCopy(props);

    // Add properly-named license files.
    init.addLicenseFiles(files, props.licenses);

    // Actually copy (and process) files.
    init.copyAndProcess(files, props, {noProcess: 'libs/**'});

    // Generate package.json file, used by npm and grunt.
    init.writePackageJSON('package.json', {
      name: 'jquery-plugin',
      version: '0.0.0-ignored',
      npm_test: 'grunt qunit',
      // TODO: pull from grunt's package.json
      node_version: '>= 0.8.0',
      devDependencies: {
        'grunt-contrib-jshint': '~0.10.0',
        'grunt-contrib-qunit': '~0.2.0',
        'grunt-contrib-concat': '~0.3.0',
        'grunt-contrib-uglify': '~0.2.0',
        'grunt-contrib-watch': '~0.4.0',
        'grunt-contrib-clean': '~0.4.0',
      },
    });

    // Generate jquery.json file.
    init.writePackageJSON(props.jqueryjson, props, function(pkg, props) {
      // The jQuery site needs the "bugs" value as a string.
      if ('bugs' in props) { pkg.bugs = props.bugs; }
      return pkg;
    });

    // All done!
    done();
  });

};
```
具体示例请参考[https://github.com/hxshandle/grunt-init-weixin-jssdk](https://github.com/hxshandle/grunt-init-weixin-jssdk)

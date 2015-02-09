title: Web开发人员的sublime text配置
date: 2014-12-08 20:42:12
tags:
- 编辑器

---

## 为什么选择Sublime Text

虽然Sublime Text一直都不是我的主开发编辑器（我的主编辑器是VIM），但是这并不妨碍我对它的喜欢，甚至有时候我会突然离开VIM转到ST上开发某些程序，主要原因是ST可以__非常快速的进行配置已满足不同的开发环境需求__，虽然VIM也可以，但是5年下来我的TMUX+VIM开发环境快捷键已经不够用了，修改起来也慢，对于一些实验性质的开发我都懒的去配置了。

<!-- more -->
### 丰富的插件

Sublime Text拥有非常丰富的插件库，而这些库都可以直接通过Sublime Text的Package Control进行安装，这在编辑器领域可以说是一个非常大的优势，这些库基本上可以满足现在所有的软件开发需求。

### 快速

说实话Sublime Text是我使用过的第二快速的编辑器（第一名当然是VIM），实在无法想象一个编辑器在集成了如此多的插件后还能如此快速。

### 中文输入法无法跟随

可以通过安装IMESupport这个插件来解决输入法跟随的问题。

### 高度可定制化

Sublime Text另外一个非常吸引人的地方是的它的配置，它抛弃了GUI化的配置改用基于JSON的配置方式，有点不言自明，快速啊。这点有点想VIM配置，都是一个基于文本的配置文件，喜欢折腾的人可以玩的很high。

## 基于Web开发的Sublime Text配置

由于本人是web前端程序员所以我的配置当然是倾向于web开发。所以以下内容都是我自己的配置。

### 插件选择
1. EMMET
2. Nettus+ Fetch
3. Sass & SassBeauty
4. JSLint
5. AlignTab
6. j​Query
7. compare side-by-side
8. docBlockr
9. Plain​Tasks

### 用户配置文件

不要使用tab来缩进应该使用空格。

``` 
{
  "color_scheme": "Packages/Dracula Color Scheme/Dracula.tmTheme",
  "draw_white_space": "all",
  "folder_exclude_patterns":
  [
    ".svn",
    ".git",
    ".hg",
    "CVS",
    "templates_c",
    "generated"
  ],
  "font_size": 12,
  "ignored_packages":
  [
    "Vintage"
  ],
  "tab_size": 2,
  "translate_tabs_to_spaces": true
}
```
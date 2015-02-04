title: 网页-项目总结
date: 2015-02-04 14:51:30
tags:
- web
---

# 网页项目总结

这里总结了在做网页项目中的积累和总结
<!-- more -->

## 首页轮播插件
**[supersliders](https://github.com/nicinabox/superslides)**

```jade
.banner
  .slides-container
      img(src="img/lanuch/bg.jpg")
      img(src="img/lanuch/bg1.jpg")
      img(src="img/lanuch/bg.jpg")
```

```js
$("#lanuch-page .banner").superslides({
  play: 6000,//轮播周期
  animation:'fade',//效果
  pagination:false//是否显示dot分页显示
});
```

##打字机效果
HTML
```jade
.txt-panel
        h3.tx(data-text="企业简介")
        p.tx(data-text="上海西歌实业有限公司是一家集设计、生产、销售为一体的大型服饰企业，产品包括服装、鞋类、箱包、帽子、围巾等。")
        p.tx(data-text="公司成立于2005年，目前在上海，杭州，广州，成立产品研发中心，在保持现有简约时尚风格的同时，大量采用欧洲、日韩、港台面料，配以精致的剪裁，精益求精的工艺要求，将时尚、舒适、女人味、休闲风四者完美融合，把女性特有魅力表现得淋漓尽致。")
        p.tx(data-text="旗下品牌Jamor创始于2005年，2013年秋季开始实行品牌化操作，目前网点100余家，分布与江浙沪，山西，湖北，山东，福建，河南等地。2014年全新形象升级，更高端大气华丽的店铺形象，加上高性价比的款式，必定会引爆新一轮的市场热潮！")
        h3.tx(data-text="品牌故事")
        p.tx(data-text="早晨，Jane被机械的轰鸣声吵醒，推开窗，脚步匆忙的行人，一个一个消失在雾霾笼罩的街道，这个世界失去了原有的色彩。")
        p.tx(data-text="极度绝望的时侯，Jane内心那个描绘色彩、创造美丽的使者深深呼唤着她，于是Jane开启了智慧之门，萌芽了一颗创作的种子，这颗种子被心湖深处的泉水悉心滋润，逐渐成长为一颗色彩斑斓的时尚之树。")  
```
JS
```
(function($, f) {
  function Typewriter(el, opts) {
    var t = this;
    t.opts = {};
    t.el = el;
    t.opts = $.extend(t.opts, opts);

    return {
      start: function() {
        $(".tx", t).html("");
        $(".tx").each(function() {
          var sNow = $(this);
          var time = 20;
          if (!sNow.attr("data-text")) {
            sNow.attr("data-text", $.trim(sNow.text()))
          }
          sNow.html("");
          var text = sNow.attr("data-text");
          var fh = ["@", "#", "$", "%", "^", "&", "*"];

          var appText = "";
          var appNu = 0;
          var whSt = setInterval(function() {
            if (appText.length < text.length) {
              appText += fh[1];
            }
            if (appText.length > 3 && appNu < text.length) {
              appText = appText.replace(appText[appNu], text[appNu]);
              appNu++;
            }

            sNow.text(appText);

            if (appNu == text.length) {
              clearInterval(whSt);
            }
          }, time);
        });
      }
    }
  }
  $.fn.typewriter = function(o) {
    return this.each(function(index) {
      var len = this.length;
      var me = $(this);
      var instance = new Typewriter(me, o);
      me.data('typewriter' + (len > 1 ? '-' + (index + 1) : ''), instance);
    });
  }

})(window.jQuery, false);
```
使用
```
$('.txt-panel').typewriter();
$(this).data('typewriter').start();
```

## 注册全局Resize方法

```
function layout(){
  ... ...
}
// global method
registerResize(layout);
```



## 动态Gride布局
[freewall](http://vnjs.net/www/project/freewall/)

## 无限循环轮播

[jquery-simplyscroll](https://github.com/logicbox/jquery-simplyscroll.git)
参考项目jiamo lookbook

## image 填充
imagefill
```jade
#container
  img(src="xxx.png")
```

```js
$('#container').imagefill();
```


## 店铺数据结构

```javascript
var store = {
  "浙江省":{
    "杭州市":{
      "杭州市店铺1":[],
      "杭州市店铺2":[],
      "杭州市店铺3":[]
    },
    "宁波市":{
      "宁波市店铺1":[],
      "宁波市店铺2":[],
      "宁波市店铺3":[]
    },
    "温州市":{
      "温州市店铺1":[],
      "温州市店铺2":[],
      "温州市店铺3":[]
    }
  },
  "江苏省":{
    "南京市":{
      "南京市店铺1":[],
      "南京市店铺2":[],
      "南京市店铺3":[]
    },
    "苏州市":{
      "苏州市店铺1":[],
      "苏州市店铺2":[],
      "苏州市店铺3":[]
    },
    "南通市":{
      "南通市店铺1":[],
      "南通市店铺2":[],
      "南通市店铺3":[]
    }
  }
};

var imgs = ["1.png","2.png","3.png","4.png"];
var len = imgs.length;
/**
* 生成店铺内容的具体method
*/
function gen(n){
    var arr = [];
    for(var i = 0 ; i < n ; i++){
        arr.push(imgs[Math.floor( Math.random() * len )]);
    }
    return arr;
}

_.each(store,function(value,key,list){
    console.log("%s ->",key,value);
    var cities = value;
    _.each(cities,function(stores,cityName,cityList){
        console.log("  %s -> ",cityName,stores);
        _.each(stores,function(el,storeName,storeList){
            console.log("    %s -> ",storeName,el);
            store[key][cityName][storeName] = gen(5);
        });
    });
});
console.log(store);
JSON.stringify(store);


```

## JScrollPane

```
$('#news .cnt-inner .details').jScrollPane({
      verticalDragMaxHeight: 20,
      verticalGutter:20
    });
```

```scss
.jspVerticalBar{
  background: none;
  width: 26px;
  
  .jspTrack{
    background: url(../img/news/scroll-bg.png) repeat-y;

    .jspDrag{
      background: url(../img/news/drag-point.png) no-repeat 50% 50%;
      width: 26px;
    }
  }
}
```

## imageTour

图片浏览插件
```
ImageTour.show(this); 
// 修改 imgTour.js中的_show方法来修改获得image src的方式
```
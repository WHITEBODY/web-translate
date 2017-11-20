## 1 关于
+ 双击划词翻译,浏览器脚本插件，支持PDF和普通网页. 
+ 使用国内优秀翻译软件[iCIBA][1]的即划即译功能。  
+ 我做了点微小的工作，把iCIBA的即划即译功能移植到浏览器上.
+ **超级重大更新(2017/11/20):已经使用标准WebExtensionsAPI开发成扩展,版本1.0: [Web-Translate][]**
+ **重大更新(2017/11/14):重写发音代码,现可完美发音,无需flash支持**.  


**↓↓↓**  在firefox下浏览本地pdf 以及 在chrome下浏览普通网页  **↓↓↓**   

![view1](http://oz6vony8d.bkt.clouddn.com/pdf-translate-view1.jpg)      
-----------------------------
![view2](http://oz6vony8d.bkt.clouddn.com/pdf-translate-view2.jpg)  

## 2 使用说明
1. 安装浏览器插件，[violentmonkey][2](暴力猴) 或者 [greasemonkey][](油猴子) 或者 [tampermonkey][](捣蛋猴)
2. 推荐[火狐][6],因为火狐默认使用[PDF.js](http://mozilla.github.io/pdf.js/)加载本地PDF。
3. 推荐插件[violentmonkey][3],向下兼容,图标好看,界面简洁.
4. 插件安装后，新建脚本，然后把js文件里的代码全部粘贴进去，保存。
5. 按需修改url匹配模式,即可正常使用.
6. 欢迎反馈.

## 3 功能特性
1.   双击或划译取词.
2.   支持**本地PDF**的双击划译(仅firefox)。
3.   支持**普通网页**的双击划译。
4.   支持**自定义样式**,比如PDF页面背景色更改，默认苹果绿。
5.   支持**发音**(firefox和chrome)。
6.   翻译弹窗可固定。
7.   **取词开关**默认隐藏在右上角菜单(PDF模式下)。
8.   跨平台，浏览器+插件。(针对日常使用Linux的朋友)
9.   强大的url正则匹配功能。


## 4 url匹配模式简单说明(**重要**)
在js代码的开头有一行注释是:
``` javascript
// @match *://*/* 
```

这个匹配模式是匹配所有url网页.  
也许你并不像这么做,比如你只想匹配本地打开的pdf,则可以改成:  
``` javascript
 // @match file:///*/*.pdf 
```

你还可以额外指定包含和排除模式,比如:
``` javascript
// @include  https://wiki.greasespot.net/*  
// @include  http://mozilla.github.io/pdf.js/web/viewer.html    
// @include /^(http|https)://en\.people\.cn//   
```

+ 模式匹配可参考:[pattern][4] 或者 [match_patterns][]
+ 更详细的文档也可以参考 [tampermonkey-documentation][]

## 5 版本
v1.0  初始版本  
1. 添加了jQuery支持  
2. 即划即译的开关按钮隐藏在pdf页面右上角的菜单中  
3. 支持发音
2017/11/06

v1.1  
1. 重构了代码  
2. 代码模块化了,更清晰易懂  
3. 添加对chrome的网页翻译支持(尚未支持本地打开的pdf文件,因为chrome有一些安全机制在阻止外部脚本的执行).  

v1.2  
1.  修复了PDF中的字体重影问题(与PDF.js插件的css冲突的问题)  
2.  在Chrome中使用发音功能的话,需要允许网页执行flash.  

v1.2.1  
修复了chrome下浏览在线pdf时候的字体重影问题.

## 6 Why
初衷:
- Linux下阅读PDF英文文档不方便，  
- goldendict非常不错,但却不支持foxitpdf的双击取词翻译。  
- youdao dict ,只支持Debian系,浏览英文文档时我感觉也不大好用。  
- 尚未发现一款能让我满意的英文文档阅读工具（Linux下,并且对中文翻译有良好支持）。   
- 自己动手,丰衣足食.  
- 方便自己,方便他人.  

问:为什么在代码中嵌入jquery?  
答:主要是为了避免脚本冲突以及重复加载,避免对原网站造成干扰。


## 7 Chrome兼容
+ chrome下不支持**本地pdf**,因为无法匹配chrome-extension开头的地址.(chrome目前不允许匹配插件地址)
+ chrome下发音的问题已于2017/11/14通过修改发音代码解决,现可完美发音,无需flash支持,请更新脚本代码.

## 8 尚未支持的少数网页(被浏览器安全机制所阻止)
+ [sarabander][]  该网页存在较严格的代码审查,iciba官方的一些代码无法通过校验,因此在该网页上无法正常加载.
+ [github.com][]  未经github签名的脚本会被拒绝注入,并且安全策略不允许跨域访问,因此也无法正常加载.
+ 后续有时间会写成firefox和chrome的扩展,这样就可以解决以上这些棘手的问题了.


[1]:<http://open.iciba.com/?c=huayi>
[2]:<https://violentmonkey.github.io/get-it/>
[3]:<https://addons.mozilla.org/zh-CN/firefox/addon/violentmonkey/>
[4]:<https://wiki.greasespot.net/Include_and_exclude_rules>
[5]:<http://get.adobe.com/cn/flashplayer>
[6]:<https://www.mozilla.org/zh-CN/firefox/new/>
[greasemonkey]:<https://addons.mozilla.org/zh-CN/firefox/addon/greasemonkey/>
[tampermonkey]:<https://addons.mozilla.org/zh-CN/firefox/addon/tampermonkey/>
[match_patterns]:<http://code.google.com/chrome/extensions/match_patterns.html>
[tampermonkey-documentation]:<http://tampermonkey.net/documentation.php>
[sarabander]:<https://sarabander.github.io/sicp/html/index.xhtml>
[github.com]:<https://github.com>
[Web-Translate]:<https://addons.mozilla.org/zh-CN/firefox/addon/web-translate>

精选的有用CSS片段集合，你可以在30秒或更短的时间内理解这些片段。

本文属于意译而非直译，在其中也增加了一些自己的语言和理解，如果存在偏差或错误还请留言指正。

本 css 精选结合共分为5大块儿， 布局类、视觉类、动画类、交互类、其他。

更加详细的介绍还请看原英文项目 - [https://github.com/30-seconds/30-seconds-of-css](https://github.com/30-seconds/30-seconds-of-css).

### 1. 重置盒模型
-------
```
重置盒模型，使盒子的宽度和高度不受其边框(border)或填充(padding)的影响。
```
`HTML`

```html
<div class="box">border-box</div>
<div class="box content-box">content-box</div>
```
`CSS`
```css
html {
  box-sizing: border-box;
}
*,
*::before,
*::after {
  box-sizing: inherit;
}
.box {
  display: inline-block;
  width: 150px;
  height: 150px;
  padding: 10px;
  background: tomato;
  color: white;
  border: 10px solid red;
}
.content-box {
  box-sizing: content-box;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c84e22392709ed?w=1748&h=432&f=png&s=23553)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/zYOvXXy)

**说明**
* box-sizing：当元素设置为border-box时，即便设置了padding或border也不会改变元素的宽度和高度。
* box-sizing：设置inherit使元素继承父级的box-sizing规则。


**浏览器支持情况**

99.9%  [查看本条 caniuse](https://caniuse.com/#feat=css3-boxsizing)


### 2. Clearfix 清除浮动
----
无需借助辅助元素进行浮动的清除。

注意：这仅在使用float布局时才有用。实际场景中请考虑使用Flexbox布局或者网格布局。

`HTML`
```html
<div class="clearfix">
  <div class="floated">float a</div>
  <div class="floated">float b</div>
  <div class="floated">float c</div>
</div>
```

`CSS`
```css
.clearfix{
  border:solid 1px red;
}
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}
.floated {
  float: left;
  margin-left:20px;
}

```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/7/30/16c427c3342a4694?w=1868&h=106&f=png&s=8205)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/jONboNZ)

**浏览器支持情况**

100%


### 3. 不变宽高比
---
给定宽度可变的元素，它将确保其高度以响应方式保持成比例（即，其宽高比保持不变）。

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c8a14b782864c8?w=2086&h=594&f=png&s=23831)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/yLBeBZr)


`HTML`
```html
<div class="constant-width-to-height-ratio"></div>
```
`CSS`
```css
.constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.constant-width-to-height-ratio::before {
  content: '';
  padding-top: 100%;
  float: left;
}
.constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
```

**说明**
* `width:50%` 只设置父级元素的宽度
* `::before` 为父级元素定义一个伪元素
* `padding-top: 100%;` 设置伪元素的内上边距，这里的百分比的值是按照宽度计算的，所以会呈现为一个响应式的元素块。
* 此方法还允许将内容正常放置在元素内。

**浏览器支持情况**

100%

---

### 4. Display table centering 如何使用表格居中
----
使用display：table（作为flexbox的替代）使子元素在其父元素中水平垂直居。

`HTML`
```html
<div class="container">
  <div class="center"><span>Centered content</span></div>
</div>
```

`CSS`
```css
.container {
  border: 1px solid #333;
  height: 250px;
  width: 250px;
}
.center {
  display: table;
  height: 100%;
  width: 100%;
}
.center > span {
  display: table-cell;
  text-align: center;
  vertical-align: middle;
}
```


`DEMO`

![](https://user-gold-cdn.xitu.io/2019/7/30/16c42a69d378167a?w=1750&h=540&f=png&s=25395)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/JjPYqYg)


* display：table 使.center元素的行为类似于<table> HTML元素。
* 设置.center的宽高为100%，使其填满父元素。
* display：table-cell, 设置'.center > span'的table-cell允许元素表现得像HTML元素。
* text-align: center 使子元素水平居中。
* vertical-align: middle 使子元素垂直居中。

外部父级必须有固定的宽高。

**浏览器支持情况**

100%  [查看本条 caniuse](https://caniuse.com/#search=display%3A%20table)


### 5. Evenly distributed children 使子元素均匀分布
----

`HTML`
```html
<div class="evenly-distributed-children">
  <p>Item1</p>
  <p>Item2</p>
  <p>Item3</p>
</div>
```
```css
.evenly-distributed-children {
  display: flex;
  justify-content: space-between;
}
```
`DEMO`


![](https://user-gold-cdn.xitu.io/2019/8/1/16c48f7a2ccef8c2?w=1766&h=166&f=png&s=11117)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/oNvjRzX)


**说明**

* display: flex :启动flex 布局
* justify-content: space-between：


* 均匀地水平分配子元素。 第一个子元素位于左边缘，而最后一个子元素位于右边缘。
或者，使用justify-content：space-around来分配子节点周围的空间，而不是它们之间。

**浏览器支持情况**

99.5%

* 需要前缀才能获得全面支持。
[caniuse](https://caniuse.com/#feat=flexbox)

### 6. Fit image in container 让图片在容器中显示的更舒适
----

设置图像在其容器内的适合度和位置，同时保留其宽高比。 以前只能使用背景图像和background-size属性来实现。

`HTML`
```html
<img class="image image-contain" src="https://picsum.photos/600/200" />
<img class="image image-cover" src="https://picsum.photos/600/200" />
```
`CSS`
```css
.image {
  background: #34495e;
  border: 1px solid #34495e;
  width: 200px;
  height: 200px;
}
.image-contain {
  object-fit: contain;
  object-position: center;
}
.image-cover {
  object-fit: cover;
  object-position: right top;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c852044a183e5b?w=1744&h=446&f=png&s=250591)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/GRKpamm)


**说明**

* `object-fit: contain`  容器内显示整个图像，并且保持宽高比
* `object-fit: cover `  用图像填充容器，并保持宽高比
* `object-position: [x] [y]` 对图像的显示部位进行调整

**浏览器支持程度**

95.5% [caniuse](https://caniuse.com/#feat=object-fit)

### 7.Flexbox centering 使用 flexbox 居中
----
使用 flexbox 水平垂直居中其子元素

`HTML`
```html
<div class="flexbox-centering"><div class="child">Centered content.</div></div>
```
`CSS`
```css
.flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c852b3b2a3f2fa?w=1998&h=204&f=png&s=13289)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/rNBOgGg)


**说明**

* `display: flex` 启用 flex 局部
* `justify-content: center` 子元素水平居中
* `align-items: center` 子元素垂直居中

**浏览器支持程度**

99.5% （需要使用前缀）   [caniuse](https://caniuse.com/#feat=flexbox)



### 8.小技巧 - 将元素垂直居中于另一个元素。
----


`HTML`
```html
<div class="ghost-trick">
  <div class="ghosting"><p>Vertically centered without changing the position property.</p></div>
</div>
```
`CSS`
```css
.ghosting {
  height: 300px;
  background: #0ff;
}
.ghosting:before {
  content: '';
  display: inline-block;
  height: 100%;
  vertical-align: middle;
}
p {
  display: inline-block;
  vertical-align: middle;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c8537a98dc7026?w=1736&h=626&f=png&s=38041)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/ZEzbNxZ)


**说明**
使用 ：before伪元素的样式垂直对齐内联元素而不更改其position属性。

**浏览器支持程度**

99.9%  [caniuse](https://caniuse.com/#feat=inline-block)


### 9. 如何使用网格居中
----

使用网格水平垂直居中子元素.

`HTML`
```html
<div class="grid-centering"><div class="child">Centered content.</div></div>
```
`CSS`
```
.grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
  height: 100px;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c8542e72898a13?w=1688&h=230&f=png&s=14262)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/YzKybOZ)


**说明**

* `display: grid` 启用网格布局
* `justify-content: center ` 使子元素水平居中
* `align-items: center` 使子元素垂直居中

**浏览器支持程度**

92.3%  [caniuse](https://caniuse.com/#feat=css-grid)

### 10. 如何使最后一项占用剩余可用高度
----

通过为最后一个元素提供当前视口中剩余的可用空间，即使在调整窗口大小时，也可以利用可用的视口空间。

`HTML`
```html
<div class="container">
  <div>Div 1</div>
  <div>Div 2</div>
  <div>Div 3</div>
</div>
```
`CSS`
```css
html,
body {
  height: 100%;
  margin: 0;
}
.container {
  height: 100%;
  display: flex;
  flex-direction: column;
}
.container > div:last-child {
  background-color: tomato;
  flex: 1;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c854bd01d2d9dc?w=2354&h=398&f=png&s=25264)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/JjPYqzK)


**说明**

* `height: 100%`  将容器的高度设为视口的高度
* `display: flex` 启用 flex
* `flex-direction: column` 将项目的顺序设置成从上到下
* `flex-grow: 1` flexbox会将容器的剩余可用空间应用于最后一个子元素。
父级必须具有视口高度。 flex-grow：1可以应用于第一个或第二个元素，它将具有所有可用空间。

**浏览器支持程度**

99.5% 需要使用前缀  [caniuse](https://caniuse.com/#feat=flexbox)


### 11. 屏外隐藏元素
----

`HTML`
```html
<a class="button" href="http://pantswebsite.com">
  Learn More <span class="offscreen"> about pants</span>
</a>
```
`CSS`
```css
.offscreen {
  border: 0;
  clip: rect(0 0 0 0);
  height: 1px;
  margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c85545e1083050?w=1520&h=98&f=png&s=7238)
[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/PoYPvve)


**说明**
* 删除所有边框
* 使用  `clip` 隐藏元素
* 设置宽高为1px
* 使用margin：-1px取消元素的高度和宽度
* 隐藏元素的溢出
* 移除所有的padding
* 绝对定位元素，使其不占用DOM中的空间
* 


**浏览器支持程度**

100% 需要使用前缀  [caniuse](https://caniuse.com/#search=clip)
(虽然cilp已被废弃，但较新的clip-path 目前对浏览器的支持非常有限。)

### 12. 如何使用变换居中子元素
----

使用 `position: absolute and transform: translate()` 进行居中，不需要知道父级和子元素的宽高，因此它非常适合响应式应用程序。

`HTML`
```html
<div class="parent"><div class="child">Centered content</div></div>
```
`CSS`
```css
.parent {
  border: 1px solid #333;
  height: 250px;
  position: relative;
  width: 250px;
}
.child {
  left: 50%;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c855e9b040dca1?w=1754&h=540&f=png&s=25799)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/xxKwoxE)


**浏览器支持程度**

97.7% 需要使用前缀  [caniuse](https://caniuse.com/#feat=transforms2d)

### 13.截断的多行文本
----

如果文本长于一行，则将截断n行，并以渐变结束。

`HTML`
```html
<p class="truncate-text-multiline">
  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut
  labore et.
</p>
```
`CSS`
```css
.truncate-text-multiline {
  overflow: hidden;
  display: block;
  height: 109.2px;
  margin: 0 auto;
  font-size: 26px;
  line-height: 1.4;
  width: 400px;
  position: relative;
}
.truncate-text-multiline:after {
  content: '';
  position: absolute;
  bottom: 0;
  right: 0;
  width: 150px;
  height: 36.4px;
  background: linear-gradient(to right, rgba(0, 0, 0, 0), #f5f6f9 50%);
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c85618a97bd586?w=1728&h=248&f=png&s=50245)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/RwbWzWQ)


**说明**

* `overflow: hidden` 防止内容溢出
* `width: 400px` 确保元素有尺寸
* `height: 109.2px` 计算的高度值，它等于font-size * line-height * numberOfLines（在这种情况下为26 * 1.4 * 3 = 109.2）
* `height: 36.4px` 渐变容器的计算值，它等于font-size * line-height（在这种情况下为26 * 1.4 = 36.4）
* `background: linear-gradient(to right, rgba(0, 0, 0, 0), #f5f6f9 50%` 渐变从 `透明`到渐变从透明到`＃f5f6f9`


**浏览器支持程度**

97.5%   [caniuse](https://caniuse.com/#feat=css-gradients)

### 14. 画一个圆
----
使用纯CSS创建圆形。

`HTML`
```html
<div class="circle"></div>
```
`CSS`
```css
.circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c856ccfcf6960b?w=1702&h=108&f=png&s=5004)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/KKPdjMO)


**浏览器支持程度**

97.7%  [caniuse](https://caniuse.com/#feat=border-radius)

### 15. 列表计数器
----

计数器本质上是由CSS维护的变量，其值可以通过CSS规则递增以跟踪它们被使用的次数。

`HTML`
```html
<ul>
  <li>List item</li>
  <li>List item</li>
  <li>
    List item
    <ul>
      <li>List item</li>
      <li>List item</li>
      <li>List item</li>
    </ul>
  </li>
</ul>
```
`CSS`
```css
ul {
  counter-reset: counter;
}
li::before {
  counter-increment: counter;
  content: counters(counter, '.') ' ';
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c856ec56ddfb93?w=1674&h=400&f=png&s=38303)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/LYPpKWj)


**说明**
你现在可以使用任何类型的html 标签创建有序列表。

* `counter-reset` 初始化计数器，该值是计数器的名称。默认情况下，计数器从0开始。此属性还可用于将其值更改为任何特定数字。
* `counter-increment` 用于可数的元素。 一旦计数器重置初始化，计数器的值可以增加或减少。
* `counter(name, style)`显示节计数器的值。通常用于内容属性。此函数可以接收两个参数，第一个作为计数器的名称，第二个参数表示占位内容，例如`3.1`的小数点。
* CSS计数器对于制作轮廓列表特别有用，因为计数器的新实例是在子元素中自动创建的。使用counters（）函数，可以在不同级别的嵌套计数器之间插入分隔文本。

**浏览器支持程度**

99.9%  [caniuse](https://caniuse.com/#feat=css-counters)

### 16.自定义滚动条
----
`HTML`
```html
<div class="custom-scrollbar">
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit.<br />
    Iure id exercitationem nulla qui repellat laborum vitae, <br />
    molestias tempora velit natus. Quas, assumenda nisi. <br />
    Quisquam enim qui iure, consequatur velit sit?
  </p>
</div>
```
`CSS`
```css
.custom-scrollbar {
  height: 70px;
  overflow-y: scroll;
}
/* To style the document scrollbar, remove `.custom-scrollbar` */
.custom-scrollbar::-webkit-scrollbar {
  width: 8px;
}
.custom-scrollbar::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c857a1d0179d18?w=1756&h=184&f=png&s=36546)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/PoYPrjx)


**浏览器支持程度**

90.7%  [caniuse](https://caniuse.com/#feat=css-scrollbar)

### 17. 如何自定义文本选择的样式
----

`HTML`
```html
<p class="custom-text-selection">Select some of this text.</p>
```
`CSS`
```css
::selection {
  background: aquamarine;
  color: black;
}
.custom-text-selection::selection {
  background: deeppink;
  color: white;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c8592829a0f65d?w=1748&h=162&f=png&s=14583)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/jONbjKE)


**浏览器支持程度**

86.5%  [caniuse](https://caniuse.com/#feat=css-selection)


### 18. 创建动态阴影
----
创建类似于box-shadow的阴影，但基于元素本身的颜色。

`HTMl`
```html
<div class="dynamic-shadow"></div>
```
`CSS`
```css
.dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
  z-index: 1;
}
.dynamic-shadow::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c8596c5b023385?w=1692&h=372&f=png&s=95595)
[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/bGbVPxX)


**说明**
* `::after` 定义一个伪元素
* `position: absolute` 使伪元素脱离文档流并相对于父级定位
* `width: 100% and height: 100%` 对伪元素进行大小调整以填充其父元素的大小，使其大小相等。
* `background: inherit` 使伪元素继承父级的线性渐变
* `top: 0.5rem` 将伪元素相对于其父元素略微偏移。
* `filter: blur(0.4rem)` 设置伪元素模糊效果，以创建下方阴影效果。
* `opacity: 0.7` 设置伪元素透明度
* `z-index: -1` 将伪元素定位在父元素后面但在背景前面。


**浏览器支持程度**

94.2%  需要使用前缀 [caniuse](https://caniuse.com/#feat=css-filters)


### 19. Etched text 蚀刻的文字
----
创建一种效果，其中文本看起来像“蚀刻”或雕刻在背景中。
`HTML`
```html
<p class="etched-text">I appear etched into the background.</p>
```
`CSS`
```css
.etched-text {
  text-shadow: 0 2px white;
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/12/16c85a4659b3a78a?w=1722&h=198&f=png&s=24139)
[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/bGbVPzb)


**说明**
* `text-shadow: 0 2px white` 从原点位置创建一个水平偏移0px和垂直偏移2px的白色阴影。
* 背景必须比阴影更暗，效果才更明显。

**浏览器支持程度**

99.5%  需要使用前缀 [caniuse](https://caniuse.com/#feat=css-textshadow)

### 20 .Focus Within 伪类
----
如果表单中的任何子项被聚焦，则更改表单的外观。
`HTML`
```html
<div class="focus-within">
  <form>
    <label for="given_name">Given Name:</label> <input id="given_name" type="text" /> <br />
    <label for="family_name">Family Name:</label> <input id="family_name" type="text" />
  </form>
</div>
```
`CSS`
```css
form {
  border: 3px solid #2d98da;
  color: #000000;
  padding: 4px;
}
form:focus-within {
  background: #f7b731;
  color: #000000;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c88e4094c7d5cd?w=1752&h=166&f=png&s=15493)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c88e448503f4d2?w=1734&h=156&f=png&s=16105)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/zYOvgOP)


**说明**
* `伪类：：focus-within` 将对应的样式应用于父元素（任何子元素被聚焦）。 例如，表单元素内的输入元素。

**浏览器支持程度**

82.9% IE11或当前版本的Edge不支持。 [caniuse](https://caniuse.com/#feat=css-focus-within)

### 21.全屏
----
`:fullsrcreen` 全屏伪类表示浏览器处于全屏模式时显示的元素。
`HTML`
```html
<div class="container">
  <p><em>Click the button below to enter the element into fullscreen mode. </em></p>
  <div class="element" id="element"><p>I change color in fullscreen mode!</p></div>
  <br />
  <button onclick="var el = document.getElementById('element'); el.requestFullscreen();">
    Go Full Screen!
  </button>
</div>
```
`CSS`
```css
.container {
  margin: 40px auto;
  max-width: 700px;
}
.element {
  padding: 20px;
  height: 300px;
  width: 100%;
  background-color: skyblue;
}
.element p {
  text-align: center;
  color: white;
  font-size: 3em;
}
.element:-ms-fullscreen p {
  visibility: visible;
}
.element:fullscreen {
  background-color: #e4708a;
  width: 100vw;
  height: 100vh;
}
```
`DEMO`


![](https://user-gold-cdn.xitu.io/2019/8/13/16c88ec127562f07?w=1664&h=924&f=png&s=82822)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c88ec438989480?w=1858&h=544&f=png&s=69656)
[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/pozjMJN)


**说明**
* `:fullscreen` 伪类选择器用于选择和设置以全屏模式显示的元素。

**浏览器支持程度**

85.6%  

[属性详解](https://developer.mozilla.org/en-US/docs/Web/CSS/:fullscreen) 

[caniuse](https://caniuse.com/#feat=fullscreen)


### 22.渐变文字
----

为文本提供渐变颜色。

`HTML`
```html
<p class="gradient-text">Gradient text</p>
```
`CSS`
```css
.gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c88ef5b1faad23?w=1568&h=166&f=png&s=12217)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/oNvjKba)


**浏览器支持程度**

94.1%

[caniuse](https://caniuse.com/#feat=text-stroke) 

### 23.渐变跟踪
----

一种悬停效果，其中渐变跟随鼠标光标。

`HTML`
```html
<button class="button">
	<span>Hover me I'm awesome</span>
</button>
```
`CSS`
```css
body {
	display: flex;
	justify-content: center;
	align-items: center;
	min-height: 100vh;
	background: white;
}

.button {
	position: relative;
	appearance: none;
	background: #f72359;
	padding: 1em 2em;
	border: none;
	color: white;
	font-size: 1.2em;
	cursor: pointer;
	outline: none;
	overflow: hidden;
	border-radius: 100px;
	
	span {
		position: relative;
		pointer-events: none;
	}
	
	&::before {
		--size: 0;

		content: '';
		position: absolute;
		left: var(--x);
		top: var(--y);
		width: var(--size);
		height: var(--size);
		background: radial-gradient(circle closest-side, #4405f7, transparent);
		transform: translate(-50%, -50%);
		transition: width .2s ease, height .2s ease;
	}
	
	&:hover::before {
		--size: 400px;
	}
}
```
```javascript
document.querySelector('.button').onmousemove = (e) => {

	const x = e.pageX - e.target.offsetLeft
	const y = e.pageY - e.target.offsetTop

	e.target.style.setProperty('--x', `${ x }px`)
	e.target.style.setProperty('--y', `${ y }px`)
	
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c88f6adf441c1a?w=1690&h=362&f=png&s=22821)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c88f6e42d95a39?w=1632&h=364&f=png&s=62241)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/wvwKVyW)


**浏览器支持程度**

91.6%  需要使用 js  [caniuse](https://caniuse.com/#feat=css-variables) 

### 24. :not 伪类选择器
---

`:not` 伪选择器对于设置一组元素的样式非常有用，同时保留最后一个（指定的）元素的样式。

`HTML`
```html
<ul class="css-not-selector-shortcut">
  <li>One</li>
  <li>Two</li>
  <li>Three</li>
  <li>Four</li>
</ul>
```
`CSS`
```css
.css-not-selector-shortcut {
  display: flex;
}
ul {
  padding-left: 0;
}
li {
  list-style-type: none;
  margin: 0;
  padding: 0 0.75rem;
}
li:not(:last-child) {
  border-right: 2px solid #d2d5e4;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c88f9d6497fe4a?w=1614&h=174&f=png&s=11971)

[可在 CodePen 上查看真实效果和编辑代码](https://codepen.io/bigerfe-com/pen/oNvjKMR)

**说明**

* `li:not(:last-child)` 设置除last：child之外的所有li元素的样式，所以最后一个元素右侧没有 border.

浏览器支持程度

99.9%  [caniuse](https://caniuse.com/#feat=css-sel3)

### 25.溢出滚动渐变
----

给溢出元素添加渐变，以更好地指示要滚动的内容。
`HTLM`
```html
<div class="overflow-scroll-gradient">
  <div class="overflow-scroll-gradient__scroller">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. <br />
    Iure id exercitationem nulla qui repellat laborum vitae, <br />
    molestias tempora velit natus. Quas, assumenda nisi. <br />
    Quisquam enim qui iure, consequatur velit sit? <br />
    Lorem ipsum dolor sit amet consectetur adipisicing elit.<br />
    Iure id exercitationem nulla qui repellat laborum vitae, <br />
    molestias tempora velit natus. Quas, assumenda nisi. <br />
    Quisquam enim qui iure, consequatur velit sit?
  </div>
</div>
```
`CSS`
```css
.overflow-scroll-gradient {
  position: relative;
}
.overflow-scroll-gradient::after {
  content: '';
  position: absolute;
  bottom: 0;
  width: 240px;
  height: 25px;
  background: linear-gradient(
    rgba(255, 255, 255, 0.001),
    white
  ); /* transparent keyword is broken in Safari */
  pointer-events: none;
}
.overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px;
  line-height: 1.2;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c891cae8be85c1?w=1742&h=448&f=png&s=70380)
[CodePen上查看和编辑代码](https://codepen.io/bigerfe-com/pen/VwZvMaa)


**说明**
* `::after`  定义一个伪元素用来展示渐变效果
* `background-image: linear-gradient(...)` 添加一个从透明变为白色（从上到下）的线性渐变。
* `pointer-events: none` 指定伪元素不能是鼠标事件的目标，后面的文本仍然是可选择/交互的。

浏览器支持程度

97.5%  [caniuse](https://caniuse.com/#feat=css-gradients)


### 26.给文字添加漂亮的下划线
----

`HTML`
```html
<p class="pretty-text-underline">Pretty text underline without clipping descending letters.</p>
```
`CSS`
```css
.pretty-text-underline {
  display: inline;
  text-shadow: 1px 1px #f5f6f9, -1px 1px #f5f6f9, -1px -1px #f5f6f9, 1px -1px #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: bottom;
  background-repeat: no-repeat;
  background-size: 100% 1px;
}
.pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
.pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c8924bebfd3769?w=1670&h=94&f=png&s=19606)
[CodePen上查看和编辑代码](https://codepen.io/bigerfe-com/pen/bGbVogv)


浏览器支持程度

97.5% [caniuse1](https://caniuse.com/#feat=css-textshadow) [caniuse2](https://caniuse.com/#feat=css-gradients)


### 27. 重置所有样式
----

使用一个属性将所有样式重置为默认值。 这不会影响`direction`和`unicode-bidi`属性。

`HTML`
```html
<div class="reset-all-styles">
  <h5>Title</h5>
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui
    repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui
    iure, consequatur velit sit?
  </p>
</div>
```
`CSS`
```css
.reset-all-styles {
  all: initial;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c892af3807918b?w=1708&h=282&f=png&s=50281)

[CodePen上查看和编辑代码](https://codepen.io/bigerfe-com/pen/gOYaGWx)

**说明**

`all` 属性允许您将所有样式（继承或不继承）重置为默认值。


浏览器支持程度

91.2% [caniuse](https://caniuse.com/#feat=css-all) 


### 28. 形状分隔符
----
使用SVG形状分割两个不同的块以创建更有趣的视觉外观。

`HTML`
```html
<div class="shape-separator"></div>
```
`CSS`
```css
.shape-separator {
  position: relative;
  height: 48px;
  background: #333;
}
.shape-separator::after {
  content: '';
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 12'%3E%3Cpath d='m12 0l12 12h-24z' fill='%23fff'/%3E%3C/svg%3E");
  position: absolute;
  width: 100%;
  height: 12px;
  bottom: 0;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89436a7d5f729?w=1746&h=130&f=png&s=6593)

[CodePen上查看和编辑代码](https://codepen.io/bigerfe-com/pen/vYBNejZ)

**说明**

* `background-image: url(...)`添加SVG形状（24x12三角形）作为伪元素的背景图像，默认情况下重复。 它必须与要分割的块颜色相同。对于其他形状，我们可以使用[SVG的URL编码器](http://yoksel.github.io/url-encoder/)。



浏览器支持程度

99.7%  [caniuse](https://caniuse.com/#feat=svg)



### 29. 系统字体
----
`HTML`
```html
<p class="system-font-stack">This text uses the system font.</p>
```
`CSS`
```css
.system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu,
    Cantarell, 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c8968f4d2e6fcf?w=1480&h=158&f=png&s=13630)

[CodePen上查看和编辑代码](https://codepen.io/bigerfe-com/pen/VwZvrwr)

**说明**
浏览器会对字体进行逐个查找，如果找到的话就是用当前的，如果找不到字体（在系统上或在CSS中定义），则继续往后查找。

* `-apple-system`在iOS和macOS上使用（但不是Chrome)
* `BlinkMacSystemFont` 用于macOS Chrome
* `Segoe UI` 用于Windows 10
* `Roboto` 在Android上使用
* `Oxygen-Sans` 在Linux KDE上使用
* `Ubuntu` 用于Ubuntu
* `Cantarell` 在GNOME Shell的Linux上使用
* `Helvetica Neue and Helvetica` 用于macOS 10.10及更低版本
* `Arial` 操作系统广泛支持的字体
* `sans-serif` 如果不支持其他任何字体，则降级使用 sans-serif 通用字体


浏览器支持程度 100%


### 30. 开关
----
只使用 css 来实现

`HTMl`
```html
<input type="checkbox" id="toggle" class="offscreen" /> <label for="toggle" class="switch"></label>
```
`CSS`
```css
.switch {
  position: relative;
  display: inline-block;
  width: 40px;
  height: 20px;
  background-color: rgba(0, 0, 0, 0.25);
  border-radius: 20px;
  transition: all 0.3s;
}
.switch::after {
  content: '';
  position: absolute;
  width: 18px;
  height: 18px;
  border-radius: 18px;
  background-color: white;
  top: 1px;
  left: 1px;
  transition: all 0.3s;
}
input[type='checkbox']:checked + .switch::after {
  transform: translateX(20px);
}
input[type='checkbox']:checked + .switch {
  background-color: #7983ff;
}
.offscreen {
  position: absolute;
  left: -9999px;
}
```

`DEMO` 

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89768980c8c6c?w=1522&h=102&f=png&s=4484)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c8976acfa3d236?w=1544&h=94&f=png&s=4235)

[CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/vYBNWEd)



浏览器支持程度 **97.7%**  需要使用前缀 

[caniuse](https://caniuse.com/#feat=transforms2d) 

### 31. 使用 css 画一个三角形
----
`HTML`
```html
<div class="triangle"></div>
```
`CSS`
```css
.triangle {
  width: 0;
  height: 0;
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c897ae6f492420?w=1624&h=82&f=png&s=3039)
[CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/XWrmzmK)

浏览器支持程度  100%；

### 32. 斑马条纹列表
----
创建具有交替背景颜色的列表，这对于区分各行间的内容很有用。

`HTML`
```html
<ul>
  <li>Item 01</li>
  <li>Item 02</li>
  <li>Item 03</li>
  <li>Item 04</li>
  <li>Item 05</li>
</ul>
```
`CSS`
```css
li:nth-child(odd) {
  background-color: #eee;
}
```

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c8992400806d02?w=1644&h=358&f=png&s=27995)

[CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/dybYZWd)

浏览器支持程度 99.9%  [caniuse](https://caniuse.com/#feat=css-sel3)

### 33.弹跳 loading 动画
----
`HTML`
```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```
`CSS`
```css
@keyframes bouncing-loader {
  to {
    opacity: 0.1;
    transform: translate3d(0, -1rem, 0);
  }
}
.bouncing-loader {
  display: flex;
  justify-content: center;
}
.bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c899584baaa4d7?w=1672&h=256&f=png&s=10935)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c8995a9482f8e2?w=1700&h=282&f=png&s=11374)

[CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/jONbaLE)

浏览器支持程度97.4%  [caniuse](https://caniuse.com/#feat=css-animation)

### 34. 按钮边框动画
----
创建一个鼠标悬停的边框动画

`HTML`
```html
<div class="button-border"><button class="button">Submit</button></div>
```
`CSS`
```css
.button {
  background-color: #c47135;
  border: none;
  color: #ffffff;
  outline: none;
  padding: 12px 40px 10px;
  position: relative;
}
.button:before,
.button:after {
  border: 0 solid transparent;
  transition: all 0.25s;
  content: '';
  height: 24px;
  position: absolute;
  width: 24px;
}
.button:before {
  border-top: 2px solid #c47135;
  left: 0px;
  top: -5px;
}
.button:after {
  border-bottom: 2px solid #c47135;
  bottom: -5px;
  right: 0px;
}
.button:hover {
  background-color: #c47135;
}
.button:hover:before,
.button:hover:after {
  height: 100%;
  width: 100%;
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89990a8585d8f?w=1512&h=134&f=png&s=7625)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c899925f837a0c?w=1526&h=130&f=png&s=7418)

[CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/RwbWjLY)

**说明**
使用：before和：after伪元素作为在悬停时设置动画的边框。

浏览器支持程度 100%.

### 35.甜甜圈旋转器
----
创建一个甜甜圈旋转器，可用于等待内容的加载。

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c899bd6b7f1b08?w=1666&h=126&f=png&s=7178)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c899bf53162468?w=1618&h=126&f=png&s=7115)

`HTML`
```html
<div class="donut"></div>
```
`CSS`
```css
@keyframes donut-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.donut {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: donut-spin 1.2s linear infinite;
}
```
[CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/NWKGwyK)

**说明**
对于整个元素使用半透明边框，然后设置一侧的边框颜色 `border-left-color: #7983ff;`,最后使用动画旋转整个元素。

浏览器支持程度** 97.4%** 需要使用前缀。

[caniuse1 https://caniuse.com/#feat=transforms2d](https://caniuse.com/#feat=css-animation) 

[caniuse2 feat=transforms2d ](https://caniuse.com/#feat=transforms2d)

### 36.缓动变量
----
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89a69309924c6?w=1590&h=194&f=png&s=8711)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89a6b729cd493?w=1706&h=198&f=png&s=17267)

`HTML`
```html
<div class="easing-variables">Hover</div>
```
`CSS`
```css
:root {
  /* Place variables in here to use globally */
}
.easing-variables {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);
  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);
  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
  display: inline-block;
  width: 75px;
  height: 75px;
  padding: 10px;
  color: white;
  line-height: 50px;
  text-align: center;
  background: #333;
  transition: transform 1s var(--ease-out-quart);
}
.easing-variables:hover {
  transform: rotate(45deg);
}
```

[CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/gOYaXjy)

浏览器支持程度** 91.6% **   [caniuse css-variables](https://caniuse.com/#feat=)

### 37.高度过度
----
当元素的高度未知时，将元素的高度从0转换为自动。

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89aa565c7dc9e?w=1580&h=94&f=png&s=13995)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89aa79f1568be?w=1690&h=148&f=png&s=19183)

[动画效果可在CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/qBWOVJo)

`HTML`
```html
<div class="trigger">
  Hover me to see a height transition.
  <div class="el">content</div>
</div>
```
`CSS`
```css
.el {
  transition: max-height 0.5s;
  overflow: hidden;
  max-height: 0;
}
.trigger:hover > .el {
  max-height: var(--max-height);
}
```
`JAVASCRIPT`
```javascript
var el = document.querySelector('.el')
var height = el.scrollHeight
el.style.setProperty('--max-height', height + 'px')
```
**说明**

浏览器支持程度** 91.6% ** caniuse css-variables

* 注意：将会导致所有动画帧重排，过度中如果元素下方有大量元素，则可能会出现滞后现象。


[caninuse - css-variables](https://caniuse.com/#feat=css-variables)

[caninuse - css-transitions](https://caniuse.com/#feat=css-variables)

### 38.悬停阴影框动画
----
在文本上悬停时，在文本周围创建一个阴影框动画效果。


![](https://user-gold-cdn.xitu.io/2019/8/13/16c89b00b7f573c8?w=1462&h=124&f=png&s=6787)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89b02eefe8e3a?w=1520&h=132&f=png&s=10080)

[动画效果可在CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/rNBOJYX)

`HTML`
```html
<p class="hover-shadow-box-animation">Box it!</p>
```
`CSS`
```css
.hover-shadow-box-animation {
  display: inline-block;
  vertical-align: middle;
  transform: perspective(1px) translateZ(0);
  box-shadow: 0 0 1px transparent;
  margin: 10px;
  transition-duration: 0.3s;
  transition-property: box-shadow, transform;
}
.hover-shadow-box-animation:hover,
.hover-shadow-box-animation:focus,
.hover-shadow-box-animation:active {
  box-shadow: 1px 10px 10px -10px rgba(0, 0, 24, 0.5);
  transform: scale(1.2);
}
```

浏览器支持程度** 97.3% ** 

[caniuse - feat-transforms3d ](https://caniuse.com/#feat=transforms3d)

[caniuse - css-transitions ](https://caniuse.com/#feat=css-transitions)


### 39.悬停下滑线动画
----
当文本悬停时，创建文本下划线动画效果。

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89b70fd3a3f31?w=1660&h=160&f=png&s=14564)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89b76a188c139?w=1688&h=158&f=png&s=14596)

[动画效果可在CodePen上预览和编辑代码](https://codepen.io/bigerfe-com/pen/mdbeKeO)

`HTML`
```html
<p class="hover-underline-animation">Hover this text to see the effect!</p>
```
`CSS`
```css
.hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
```

**说明**

* `display: inline-block` 使p成为内联块，以防止下划线跨越整行宽度而不仅仅是文本内容。
* `position: relative` 设置父元素为相对定位
* `::after` 定义一个伪元素
* `position: absolute` 将伪元素脱离文档六，并将其相对于父元素定位
* `width: 100%` 确保伪元素和父元素的宽度一致。
* `transform: scaleX(0)` 最初将伪元素缩放为0，因此他是看不见的。
* `bottom: 0 and left: 0` 将伪元素放在父元素的左下角。
* `transition: transform 0.25s ease-out` 设置动画效果为`ease-out`,并且在0.25秒内完成。
* `transform-origin: bottom right` 变换中心点到父元素的右下角。
* `:hover::after` 然后使用scaleX（1）将宽度转换为100％，然后将中心点更改为左下角，允许它在悬停时从另一个方向转换出来。

浏览器支持程度** 97.5% **

[caniuse - feat=transforms2d](https://caniuse.com/#feat=transforms2d)

[caniuse - css-transitions](https://caniuse.com/#feat=css-transitions)


### 40. 禁用选择
----
使用 css 让内容无法选取。

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89c54009b4e13?w=1690&h=230&f=png&s=22079)

[可在CodePen上预览效果和编辑代码](https://codepen.io/bigerfe-com/pen/wvwKYJp)

`HTML`
```html
<p>You can select me.</p>
<p class="unselectable">You can't select me!</p>
```
`CSS`
```css
.unselectable {
  user-select: none;
}
```

**说明**

`user-select: none` 指定无法选择文本

浏览器支持程度** 93.2% ** （需要使用前缀，这并不是防止用户复制内容的安全方法。）

[caniuse - feat=user-select-none](https://caniuse.com/#feat=user-select-none)

### 41. 弹出菜单
----
在悬停和焦点上弹出交互式菜单。


![](https://user-gold-cdn.xitu.io/2019/8/13/16c89cae94d5aebc?w=1728&h=242&f=png&s=8336)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89cb0e1083c9a?w=1660&h=242&f=png&s=12923)

[可在CodePen上预览效果和编辑代码](https://codepen.io/bigerfe-com/pen/GRKpwKx)

`HTML`
```html
<div class="reference" tabindex="0"><div class="popout-menu">Popout menu</div></div>
```
`CSS`
```css
.reference {
  position: relative;
  background: tomato;
  width: 100px;
  height: 100px;
}
.popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
  background: #333;
  color: white;
  padding: 15px;
}
.reference:hover > .popout-menu,
.reference:focus > .popout-menu,
.reference:focus-within > .popout-menu {
  visibility: visible;
}
```

**说明**
* `left: 100%` 弹出菜单从左侧偏移其父级宽度的100％。
* `visibility: hidden` 
* `.reference:hover > .popout-menu`  鼠标悬停时，.popout-menu 显示
* `.reference:focus > .popout-menu` 聚焦时，.popout-menu 显示
* `.reference:focus-within > .popout-menu` 确保在焦点位于参考范围内时显示弹出窗口。
* 

浏览器支持程度 100%;

### 42.兄弟元素淡化
-----
悬停时兄弟节点淡化显示.

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89d308ac49e72?w=1702&h=98&f=png&s=12281)

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89d337260e61d?w=1628&h=98&f=png&s=13920)

[可在CodePen上预览效果和编辑代码](https://codepen.io/bigerfe-com/pen/MWgazPj)

`HTML`
```html
<div class="sibling-fade">
  <span>Item 1</span> <span>Item 2</span> <span>Item 3</span> <span>Item 4</span>
  <span>Item 5</span> <span>Item 6</span>
</div>
```
`CSS`
```css
span {
  padding: 0 1rem;
  transition: opacity 0.2s;
}
.sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
```

**说明**
* `transition: opacity 0.2s` 设置0.2秒的淡化动画。
* `.sibling-fade:hover span:not(:hover)`当父级悬停时，选择当前未悬停的span子项并将其透明度更改为0.5。

浏览器支持程度 97.5%；

[caniuse-feat=css-sel3](https://caniuse.com/#feat=css-sel3)

[caniuse-feat=css-transitions](https://caniuse.com/#feat=css-transitions)


### 43. 计算函数 Calc()
----
函数calc（）允许使用数学表达式定义CSS值，属性采用的值是数学表达式的结果。

`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89ea6a9058f6c?w=1736&h=592&f=png&s=58919)

[可在CodePen上预览效果和编辑代码](https://codepen.io/bigerfe-com/pen/BaBobXB)

如果你想在右侧和底部对齐背景图像，则只能使用直线长度值。 所以现在可以使用calc（）函数.


`HTML`
```html
<div class="box-example"></div>
```
`CSS`
```css
.box-example {
  height: 280px;
  background: #222 url('https://image.ibb.co/fUL9nS/wolf.png') no-repeat;
  background-position: calc(100% - 20px) calc(100% - 20px);
}
```

**说明**
* 允许加法，减法，乘法和除法。
* 可以为表达式中的每个值使用不同的单位（例如，像素和百分比）。
* 允许嵌套calc（）函数。
* 它可用于任何允许<length>，<frequency>，<angle>，<time>，<number>，<color>或<integer>的属性，如width，height，font-size，top等。
* 

浏览器支持程度 97.0% 

[caniuse - feat=calc](https://caniuse.com/#feat=calc)

### 44. css 自定义变量
----
包含要重用的特定值的CSS变量。

`HTML`
```html
<p class="custom-variables">CSS is awesome!</p>
```
`CSS`
```css
:root {
  /* Place variables within here to use the variables globally. */
}
.custom-variables {
  --some-color: #da7800;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray, 0 0 0.2em slategray;
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
```
`DEMO`

![](https://user-gold-cdn.xitu.io/2019/8/13/16c89f2cd1b1f056?w=1736&h=186&f=png&s=54644)

[可在CodePen上预览效果和编辑代码](https://codepen.io/bigerfe-com/pen/XWrmQaq)

**说明**
* `--variable-name:` 用这样的格式来声明变量。
* `var(--variable-name)` 使用此函数在整个文档中重用变量。

浏览器支持程度 91.6%

[caniuse - feat=css-variables](https://caniuse.com/#feat=css-variables)





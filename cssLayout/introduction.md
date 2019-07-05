## 1. CSS Layout

-   Normal flow 左右上下
-   The display property
-   Flexbox
-   Grid
-   Floats
-   Positioning: static, fixed, relative, absolute
-   Table layout
-   Multiple-column layout

## 2. 盒模型

#### 标准盒模型 <sup>1</sup>

![盒子模型](https://img-blog.csdn.net/20180619173347603?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI2NzgwMzE3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### box-sizing: border-box 修改后的盒模型 <sup>1</sup>

![border-box修改后的盒模型](https://img-blog.csdn.net/20180619174330697?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzI2NzgwMzE3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 3. 浮动和清除浮动

`float: none | left | right | inherit`

> -   浮动元素排版超出了其父级元素，父元素的高度出现了塌缩，若没有文字高度的支撑，不考虑边框，父级元素高度会塌缩成零。
> -   浮动元素甚至影响到了其父元素的兄弟元素（.bottomDiv）排版。因为浮动元素脱离了文档流，.bottomDiv 在计算元素位置的时候会忽略其影响，紧接着上一个元素的位置继续排列。<sup>2</sup>

```html
<style>
	.container {
		border: 1px dashed gray;
	}
	.float-div {
		float: left;
		background: rgba(00, 0, 255, 0.3);
		height: 200px;
		width: 200px;
	}

	.text-div {
		font-weight: bold;
	}
</style>

<div class="container">
	<div class="float-div"></div>
	<div class="text-div">Text text text text</div>
</div>
```

![浮动](https://s2.ax1x.com/2019/07/03/ZtsUtx.png)

1. 增加**clear**

```html
<style>
	.container {
		border: 1px dashed gray;
	}
	.float-div {
		float: left;
		background: rgba(00, 0, 255, 0.3);
		height: 200px;
		width: 200px;
	}
	.text-div {
		clear: left;
	}
</style>

<div class="container">
	<div class="float-div"></div>
	<div class="text-div">Text text text text</div>
</div>
```

2. 父级元素末尾添加块级元素

```html
<style>
	.container {
		border: 1px dashed gray;
	}
	.float-div {
		float: left;
		background: rgba(00, 0, 255, 0.3);
		height: 200px;
		width: 200px;
	}
	.clear-left {
		clear: left;
	}
</style>

<div class="container">
	<div class="float-div"></div>
	<div class="text-div">Text text text text</div>
	<div class="clear-left"></div>
</div>
```

3. 利用伪元素

```html
<style>
	.container {
		border: 1px dashed gray;
	}
	.float-div {
		float: left;
		background: rgba(00, 0, 255, 0.3);
		height: 200px;
		width: 200px;
	}
	.clearfix:after {
		content: ' ';
		display: table;
		clear: both;
	}
</style>

<div class="container clearfix">
	<div class="float-div"></div>
	<div class="text-div">Text text text text</div>
</div>
```

清除效果：
![清除浮动效果](https://s2.ax1x.com/2019/07/03/Ztsf9f.png)

## 3. References

[CSS Website Layout](https://www.w3schools.com/css/css_website_layout.asp)

[学习 CSS 布局](http://zh.learnlayout.com/)

[The Different Kinds of CSS Layout](https://css-tricks.com/guides/layout/)

[Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

[Flex 布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)

[CSS Grid 网格布局教程](http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html)

## 4. 一个新闻网页

-   搜索栏
-   菜单/分类

-   头条/置顶新闻
-   箭头

-   次分类/区域
-   摘要图片
-   标题
-   摘要文字
-   时间与作者
-   视频

-   尾部

---

引用

-   1. [从 box-sizing:border-box 属性入手，来了解盒模型](https://blog.csdn.net/qq_26780317/article/details/80736514)
-   2. [清除浮动的四种方式及其原理理解](https://segmentfault.com/p/1210000011625576/read)

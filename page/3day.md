<!--
 * @Author: wujiewei 619673401@qq.com
 * @Date: 2024-01-03 08:29:29
 * @LastEditors: wujiewei 619673401@qq.com
 * @LastEditTime: 2024-01-03 10:16:24
 * @FilePath: /frontEnd/page/3dat.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# CSS 盒模型以及常见布局
> 在 CSS 中，所有的元素都被一个个的 “盒子（box）” 包围着，我们广泛地使用两种“盒子” —— 块级盒子 (block box) 和 内联盒子 (inline box)

1. 什么是 CSS 盒模型 ？
> 在 CSS 中，盒模型（box model）是在设计和布局时使用.
盒模型的定义可以分成几部分组成：
- Content box: 这个区域是用来显示内容，大小可以通过设置 width 和 height.
- Padding box: 包围在内容区域外部的空白区域； 大小通过 padding 相关属性设置。
- Border box: 包裹内容和内边距。大小通过 border 相关属性设置。
- Margin box: 这是最外面的区域，是盒子和其他元素之间的空白区域。大小通过 margin 相关属性设置。
![Alt](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/dd9147d32262427e8cd1c8b78b886c29~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

>块级盒子完整地应用了 CSS 盒模型，内联盒子只使用盒模型中定义的部分内容。

### 与盒模型相关的几个CSS属性需要熟练并运用的

#### box-sizing 
box-sizing 属性定义了浏览器应该如何计算一个元素的总宽度和总高度。
- content-box（默认值），即标准盒模型，width: 100px 指的是内容区会有 100px 宽。
    - 盒子的大小 = content(100px) + padding + border
- border-box，即替代（IE）盒模型，width: 100px 指的是 内容区 + 边框 + 内边距 的总和是 100px 宽。
    - 盒子的大小 = content + padding + border = 100px
> 不论那种模型，margin 都是不计入实际大小 —— 当然，它会影响盒子在页面所占空间，但是影响的是盒子外部空间。

#### display
display 属性定义了元素的盒模型的展示形式。
- none： 隐藏值 常用于隐藏盒子
    - 隐藏的盒子不会在文档流中占据任何空间
- block： 块元素
- inline: 内联元素
- flex: 弹性盒子
- grid: 网格布局
> 本节达成的目标需要知道一个盒子是如何计算他的长宽总数
2. BFC、IFC、FFC、GFC
#### Formatting Context（格式化上下文）
> Formatting context 是 W3C CSS2.1 规范中的一个概念。它是页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。

> BFC是一个独立的布局环境，其中的元素布局是不受外界的影响，并且在一个BFC中，块盒与行盒（行盒由一行中所有的内联元素所组成）都会垂直的沿着其父元素的边框排列。

#### Formatting Context（格式化上下文）包括
1. BFC (块级)
2. IFC 
3. FFC
4. GFC

### BFC
> BFC(Block formatting context)直译为"块级格式化上下文"。它是一个独立的渲染区域，只有Block-level box参与， 它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相干。

#### BFC的布局规则
- 内部的Box会在垂直方向，一个接一个地放置。

- Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠。

- 每个盒子（块盒与行盒）的margin box的左边，与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。

- BFC的区域不会与float box重叠。

- BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。

- 计算BFC的高度时，浮动元素也参与计算。

#### 如何创建BFC
1. float的值不是none。
2. position的值不是static或者relative
3. display的值是inline-block、table-cell、flex、table-caption或者inline-flex
4. overflow的值不是visible。

#### BFC的作用
- 利用BFC避免margin重叠。

### IFC
> IFC(Inline Formatting Contexts)直译为"内联格式化上下文"，IFC的line box（线框）高度由其包含行内元素中最高的实际高度计算而来（不受到竖直方向的padding/margin影响)
IFC中的line box一般左右都贴紧整个IFC，但是会因为float元素而扰乱。float元素会位于IFC与与line box之间，使得line box宽度缩短。 同个ifc下的多个line box高度会不同。 IFC中时不可能有块级元素的，当插入块级元素时（如p中插入div）会产生两个匿名块与div分隔开，即产生两个IFC，每个IFC对外表现为块级元素，与div垂直排列。
那么IFC一般有什么用呢？
水平居中：当一个块要在环境中水平居中时，设置其为inline-block则会在外层产生IFC，通过text-align则可以使其水平居中。
垂直居中：创建一个IFC，用其中一个元素撑开父元素的高度，然后设置其vertical-align:middle，其他行内元素则可以在此父元素下垂直居中。

#### IFC布局规则
框会从包含块的顶部开始，一个接一个地水平摆放。
摆放这些框的时候，它们在水平方向上的外边距、边框、内边距所占用的空间都会被考虑在内。在垂直方向上，这些框可能会以不同形式来对齐：它们可能会把底部或顶部对齐，也可能把其内部的文本基线对齐。能把在一行上的框都完全包含进去的一个矩形区域，被称为该行的行框。水平的margin、padding、border有效，垂直无效。不能指定宽高。
行框的宽度是由包含块和存在的浮动来决定。行框的高度由行高计算这一章所描述的规则来决定。

### FFC 
> FFC(Flex Formatting Contexts)直译为"自适应格式化上下文"，display值为flex或者inline-flex的元素将会生成自适应容器（flex container），可惜这个牛逼的属性只有谷歌和火狐支持，不过在移动端也足够了，至少safari和chrome还是OK的，毕竟这俩在移动端才是王道。
Flex Box 由伸缩容器和伸缩项目组成。通过设置元素的 display 属性为 flex 或 inline-flex 可以得到一个伸缩容器。设置为 flex 的容器被渲染为一个块级元素，而设置为 inline-flex 的容器则渲染为一个行内元素。
伸缩容器中的每一个子元素都是一个伸缩项目。伸缩项目可以是任意数量的。伸缩容器外和伸缩项目内的一切元素都不受影响。简单地说，Flexbox 定义了伸缩容器内伸缩项目该如何布局。

### GFC
> GFC(GridLayout Formatting Contexts)直译为"网格布局格式化上下文"，当为一个元素设置display值为grid的时候，此元素将会获得一个独立的渲染区域，我们可以通过在网格容器（grid container）上定义网格定义行（grid definition rows）和网格定义列（grid definition columns）属性各在网格项目（grid item）上定义网格行（grid row）和网格列（grid columns）为每一个网格项目（grid item）定义位置和空间。
那么GFC有什么用呢，和table又有什么区别呢？首先同样是一个二维的表格，但GridLayout会有更加丰富的属性来控制行列，控制对齐以及更为精细的渲染语义和控制。

# 布局
### 经典的布局典型的案例 有圣杯布局 与 双飞翼布局
> 圣杯布局来源于文章In Search of the Holy Grail，而双飞翼布局来源于淘宝UED。

虽然两者的实现方法略有差异，不过都遵循了以下要点：

- 两侧宽度固定，中间宽度自适应
- 中间部分在DOM结构上优先，以便先行渲染
- 允许三列中的任意一列成为最高列
- 只需要使用一个额外的 div 标签

效果图如下：
![Alt](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6ae729ef74d24dab9e9ed46a712d039e~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)

#### 区别
#### 1.圣杯布局：
-   布局结构清晰，一目了然
-   为了让中间div内容不被遮挡，将中间div设置了左右padding-left和padding-right后，将左右两个div用相对布局position: relative并分别配合right和left属性，以便左右两栏div移动后不遮挡中间div。
#### 2. 双飞翼布局：
-   布局结构不太直观
-   为了让中间div内容不被遮挡，直接在中间div内部创建子div用于放置内容，在该div里用margin-left和margin-right为左右两栏div留出位置。

## 圣杯布局：
用float 实现
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>圣杯布局</title>
		<style>
			* {
				margin: 0;
				padding: 0;
				font-size: 25px;
				text-align: center;
			}

			header,
			footer {
				height: 40px;
				width: 100%;
				background: skyblue;
			}

			footer {
				clear: both;
			}

			.wrapper {
				padding: 0 300px 0 150px;
				height: 100px;
			}

			.center {
				float: left;
				width: 100%;
				height: 500px;
				background: plum;

			}

			.left {
				float: left;
				width: 150px;
				height: 500px;
				margin-left: -100%;
				position: relative;
				left: -150px;
				background: pink;
			}

			.right {
				float: left;
				width: 300px;
				height: 500px;
				margin-left: -300px;
				position: relative;
				right: -300px;
				background: hotpink;
			}
		</style>
	</head>
	<body>
		<header>header</header>
		<div class="wrapper">
			<div class="center">center</div>
			<div class="left">left</div>
			<div class="right">right</div>
		</div>
		<footer>footer</footer>
	</body>
</html>
```
其中：
左右栏通过添加负的margin放到正确的位置了，此段代码是为了摆正中间栏的位置
```css
.wrapper {
	padding: 0 300px 0 150px;
	height: 100px;
}
```
中间栏的位置摆正之后，左栏的位置也相应右移，通过相对定位的left恢复到正确位置
```css
.left {
	float: left;
	width: 150px;
	margin-left: -100%;
	position: relative;
	left: -150px;
}
```
中间栏的位置摆正之后，右栏的位置也相应左移，通过相对定位的right恢复到正确位
```css
.right {
	float: left;
	width: 300px;
	margin-left: -300px;
	position: relative;
	right: -300px;
}
```
优点：不需要添加dom节点

## 双飞翼布局
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>双飞翼布局</title>
		<style>
			* {
				margin: 0;
				padding: 0;
				font-size: 25px;
				text-align: center;
			}

			header,
			footer {
				height: 40px;
				width: 100%;
				background: skyblue;
			}

			footer {
				clear: both;
			}

			.center {
				float: left;
				width: 100%;
				/*左栏上去到第一行*/
				height: 500px;
				background: plum;
			}

			/*给内部 div 添加 margin，把内容放到中间栏，其实整个背景还是 100%*/
			#inside {
				margin: 0 300px 0 150px;
				height: 500px;
			}

			.left {
				float: left;
				width: 150px;
				height: 500px;
				margin-left: -100%;
				background: pink;
			}

			.right {
				float: left;
				width: 300px;
				height: 500px;
				margin-left: -300px;
				background: hotpink;
			}
		</style>
	</head>
	<body>
		<header>header</header>
		<div class="center">
			<div class="inside">center</div>
		</div>
		<div class="left">left</div>
		<div class="right">right</div>
		<footer>footer</footer>
	</body>
</html>
```
优点：不会像圣杯布局那样变形; 缺点是：多加了一层dom节点

# 普通三栏布局，其中左右两栏宽度固定,中间自适应。
通过实践，发现flex布局和grid布局真香。
## 利用flex
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>圣杯布局</title>
		<style>
			* {
				margin: 0;
				padding: 0;
				font-size: 25px;
				text-align: center;
			}

			header,
			footer {
				height: 40px;
				width: 100%;
				background: skyblue;
			}

			.wrapper {
				display: flex;
			}

			.left {
				width: 150px;
				height: 500px;
				background: pink;
			}
			
			.center {
				flex: 1;
				height: 500px;
				background: plum;
			}

			.right {
				width: 300px;
				height: 500px;
				background: hotpink;
			}
		</style>
	</head>
	<body>
		<header>header</header>
		<div class="wrapper">
			<div class="left">left</div>
			<div class="center">center</div>
			<div class="right">right</div>
		</div>
		<footer>footer</footer>
	</body>
</html>
```
## grid布局
实现效果
![Alt](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/19ef7bf64e7049d2b14d32f51ea89638~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp)
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>圣杯布局</title>
		<style>
			body {
				display: grid;
				grid-template-areas:
					'header header header'
					'left center right'
					'footer footer footer';
				min-height: 100vh;
				grid-template-rows: 40px 1fr 40px;
				grid-template-columns: 150px 1fr 300px;
				font-size: 25px;
				text-align: center;
			}

			header {
				grid-area: header;
				background: skyblue;
			}

			footer {
				grid-area: footer;
				background: skyblue;
			}

			.left {
				grid-area: left;
				background: pink;
			}

			.center {
				grid-area: center;
				background: plum;
			}

			.right {
				grid-area: right;
				background: hotpink;
			}
		</style>
	</head>
	<body>
		<header>header</header>
		<div class="left">left</div>
		<div class="center">center</div>
		<div class="right">right</div>
		<footer>footer</footer>
	</body>
</html>
```
grid布局非常灵活，对于这种布局的实现有很多种方式。笔者这里先给出最直观的一种，足以体现grid的强大。

> 四种布局都用典型的例子写完，其中两种传统布局 后者则为现在最流行的，传统布局方式为了当时兼容的IE浏览器

弹性盒子布局学习链接：
语法篇： https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html 
实战篇： https://www.ruanyifeng.com/blog/2015/07/flex-examples.html 

网格布局学习链接：
https://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html
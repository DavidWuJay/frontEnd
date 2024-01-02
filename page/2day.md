# CSS篇章
> 什么是CSS？ CSS: 层叠样式表，简称CSS 是一种样式表语言，用来描述 HTML 或 XML（包括SVG、MathML 或 XHTML之类的XML 分支语言）文档的呈现方式。 CSS 描述了在屏幕、纸质、音频等其他媒体上的元素应该如何背渲染问题。

1. 如何在HTML中声明CSS
- 标签内部描述例子如下：

```css
<div style="border:1px; background:red; "></div>
```

- 通过style标签

```html
<!DOCTYPE html>
<html>
    <head>
        <style>
            .container {
                background: red;
                border: 1px;
            }
        </style>
    </head>
    <body>
        <div class="container"></div>
    </body>
</html>
```

- 成立样式表，第三种方式也是最优的

```css
            .container {
                background: red;
                border: 1px;
            }
```

```html
<!DOCTYPE html>
<html>
    <head>
        <link src='./style.css'>
    </head>
    <body>
        <div class="container"></div>
    </body>
</html>
```

2. 选择器
> 选择器分为6大类： 基本选择器、属性选择器、关系选择器、伪元素选择器、伪类选择器。其实对于选择器的种类我们不必死记硬背，用多了自然就会记住了

- 基本选择器
### 通配符选择器（*）
通配符选择器（*）用于选择所有的元素。示例如下
```
* {
    padding: 0;
    margin: 0;
}
```

### ID选择器（#id）
ID选择器 以 # 开头，后面紧接着元素的 id
```
#app {
    color: black;
    font-size: 14px;
}
```

### 类名选择器(.class)
类名选择器 又叫做 class选择器，以 . 开头，后面紧接着元素的 class。下面示例代码用于设置 class 为 content 的元素的样式：
```
.content {
    min-width: 100px;
    min-height: 100px;
    border-radius: 4px;
    background-color: #fff;
}
```
### 标签选择器/元素选择器(div)
标签选择器 又叫做 元素选择器，命名格式为标签名（元素名），例如：p 和 div。下面示例代码用于设置所有的 P 元素的样式
```
p {
    margin: 1em 0;
    text-indent: 2em;
}
```
### 属性选择器
```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>CSS属性选择器测试</title>
    <link rel="stylesheet" href="./style.css">
</head>
<body>
    <div data-title="true">《关雎》</div>
    <div data="aa">关关雎鸠，在河之洲。窈窕淑女，君子好逑。</div>
    <div data="aa bb">参差荇菜，左右流之。窈窕淑女，寤寐求之。</div>
    <div data="aa-bb">求之不得，寤寐思服。悠哉悠哉，辗转反侧。</div>
    <div data="aabb">参差荇菜，左右采之。窈窕淑女，琴瑟友之。</div>
    <div data="bbaacc">参差荇菜，左右芼之。窈窕淑女，钟鼓乐之。</div>
</body>
</html>
```
![Alt](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3b510d103e4d44dd873f27d496c13b8d~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)
### [attribute]
[data-title] 这就是一个属性选择器，用于选择 含有 data-title 属性 的元素。下面是使用该选择器的示例代码:
```
/* 将含有 data-title 属性的元素的字体颜色设置为红色 */
[data-title] {
    color: red;
}
```
页面效果如下：
![Alt](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5f2fb8def90343cb906794a14dca557f~tplv-k3u1fbpfcp-zoom-in-crop-mark:1512:0:0:0.awebp?)
### 伪元素选择器
伪元素主要用于指定某些元素的特定部分，以表示无法用 HTML 语义表达的实体。与此不同，伪类主要用于区分元素的不同状态或行为。通常情况下，伪元素前面是 ::，包含两个英文冒号；而伪类前面只有一个英文冒号 :。然而，不能单纯通过这个属性来判断是伪元素还是伪类，因为在 CSS2 中，伪元素和伪类都使用单个冒号，在 CSS3 中，为了区分伪元素和伪类，引入了双冒号 :: 的表示法。不过，浏览器仍然接受由 CSS2 引入的单冒号 : 的写法。
### 伪类选择器
伪元素主要用于指定某些元素的特定部分，伪类主要是用来区分元素的不同状态或者行为。
### #:root
选中文档的根元素。对于 HTML 来说，:root 表示 <html> 元素，除了优先级更高之外，与 <html> 选择器相同。在声明全局 CSS 变量时 :root 会很有用
```css
:root {
    --background-color: #fff;
}

```
### 常见组合选择器
- 后代选择器(selectorA selectorB)
后代选择器可以选择作为某元素后代的元素，也可以是两个以上的选择器，多个选择器之间用空格分隔。
```css
/* 选择 <ol> 元素内部所有的 <li> 元素 */
ol li {
    color: red;
}
```
- 子元素选择器(selectorA > selectorB)
与后代选择器相比，子元素选择器（Child selectors）只能选择作为某元素子元素的元素（中间的空格可以不要）。
```css
/* 选择直系父元素为 <div> 元素的 <p> 元素  */
div > p {
    color: red;
}
```
- 相邻兄弟选择器(selectorA + selectorB)
```css
/* 选择上一个选择器为 <div> 元素的 <p> 元素 */
div + p {
    color: red;
}

```
- selectorA ~ selectorB
```css
/* 将 <div> 元素后面的 <p> 元素的字体颜色设置为红色 */
div ~ p {
    color: red;
}
匹配上面样式规则的元素必须要满足下面所有条件：

<p> 元素排在 <div> 元素后面（不一定要紧接着）。
<p> 元素和 <div> 元素是兄弟元素，具有同一个父元素。
```
- selectorAselectorB
匹配同时满足两个规则 selectorA 和 selectorB 的元素，可以是两个以上的选择器，多个选择器之间不需要分隔。
```css
/* 类名为 app 的 <div> 元素 */
div.app {
    /*  */
}

/* 类名含有 app 也含有 test 的元素 */
.app.test {
    /*  */
}
```

# selectorA, selectorB
用于同时选取多个元素，多个选择器用逗号分割（逗号后面的空格可以不要）。
```css
/* 同时设置 <div> 元素和 <p> 元素的字体大小 */
div, p {
    font-size: 16px;
}
```
> 获取更详细的 参考 https://juejin.cn/post/7271835473336860732?searchId=20240102103910E9ACEBF36F4A6CCC78EA#heading-61

3. css 权重以及其计算规则
- 权重
|  选择器  | 权重  |
|  ----  | ----  |
| !important  | 	Infinity(无限大) |
| 行列样式  | 1000 |
| Id选择器  | 0100 |
| Class选择器/属性/伪类  | 0010 |
| 标签选择器  | 0001 |
| *通配符选择器  | 0000 (大于默认样式与继承验样式) |
| 继承样式  | 权重最小(比*通配符还小) |
> 注意：选择器的权重值不是一个确定的值，例如标签选择器的权重值为1，但是这个1是一个256进制数，就是0到255后+1才是1。就是说权重值2和1中间差了255。这表示256个权重值为1的选择器加一起才抵得上一个权重为2的，这在后面权重计算有用。
还有需要注意的是，！important的权重值虽然是正无穷，但其实也是可也计算的，比如正无穷+1或者*1，就是要比正无穷大，在计算机中正无穷的值，都是一个有界的。不是数学上无界的一个慨念！
- 计算规则
> 一般而言，选择器越特殊，它的优先级越高。也就是选择器指向的越准确，它的优先级就越高。单一选择器直接比较权重，多个选择器则需要计算。
复杂的计算方法：

用1表示派生选择器的优先级

用10表示类选择器的优先级

用100标示ID选择器的优先级

- div.test1 .span var 优先级 1+10 +10 +1
- span#xxx .songs li 优先级1+100 + 10 + 1
- #xxx li 优先级 100 +1
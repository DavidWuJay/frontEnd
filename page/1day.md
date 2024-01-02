<!--
 * @Author: wujiewei 619673401@qq.com
 * @Date: 2023-12-28 16:30:21
 * @LastEditors: wujiewei 619673401@qq.com
 * @LastEditTime: 2024-01-02 10:33:31
 * @FilePath: /ar-table/培训计划/1day.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# 第一天熟悉网站的构成

## 无论用Vue、React、Angular 写的代码全部会转化成Html、Css、JavaScript
- Html
假设用一个人来形容 骨架就是 相当于 Html,

- Css 
有了骨架之后 Css 充当皮肤的意思 通过不同的肤色 五官，以及塑造的衣服构建成一个人物

- JavaScript
形成了一个人之后，属于赋予这个人的大脑，通过大脑控制动作，JavaScript 就是充当这个角色。

## Html
### HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言: HyperText Markup Language
- HTML 不是一种编程语言，而是一种标记语言
- 标记语言是一套标记标签 (markup tag)
- HTML 使用标记标签来描述网页
- HTML 文档包含了HTML 标签及文本内容
- HTML文档也叫做 web 页面

### HTML 标签
- HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

- HTML 标签是由尖括号包围的关键词，比如 <html>
- HTML 标签通常是成对出现的，比如
- 标签对中的第一个标签是开始标签，第二个标签是结束标签
- 开始和结束标签也被称为开放标签和闭合标签
> HTML 标签 和 HTML 元素 叫法不同，但是含义是一样的


### 如何声明一个工作模板呢
```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
 
<h1>我的第一个标题</h1>
 
<p>我的第一个段落。</p>
 
</body>
</html>
```
### 常用的标签
```
div
p 
span 
ul 
li
ol
table
img
// html5当中
video
audio
input
form
canvas
// 语义元素
header
nav
footer
section
article
aside
```
## 重点内容区分块级元素 与 内联元素
> 块级元素： 指的是占据其父元素（容器）的整个空间，因此创建了一个“块”。通常浏览器会在块级元素前后另起一行。能容纳其他块元素或者内联元素

> 内联元素：因此创建了一个“块”。通常浏览器会在块级元素前后另起一行。能容纳其他块元素或者内联元素。 

> 二者区别：

1. 块元素，总是在新行上开始；内联元素，和其他元素在一行
2. 块元素，能容纳其他块元素或者内联元素；内联元素，只能容纳文本或其他内联元素；
3. 块元素中高度，行高以及顶和底边距都可以控制；内联元素中高，行高及顶和底边距不可改变。

> 各自的特点

1. 块元素的特点：
    - 总是在新行上开始
    - 高度、行高以及外边距和内边距都可控制
    - 宽度默认是它容器的100%，除非设定一个宽度
    - 他可以容纳内联元素和其他块元素
2. 内联元素的特点：
    - 和其他元素都在同一行
    - 高，行高及外边距和内边距不可改变
    - 宽度就是它的文字和图片的宽度，不可改变
    - 内联元素只能容纳文本或者其他内联元素

> 练一练 区分出哪些元素为块级元素，哪些为内联元素


### 标签属性
- 属性是 HTML 元素提供的附加信息。

- HTML属性
    1. HTML 元素可以设置属性
    2. 属性可以在元素中添加附加信息
    3. 属性一般描述于开始标签
    4. 属性总是以名称/值对的形式出现，比如：name="value"
    5. 属性值应该始终被包括在引号内，双引号是最常用的，不过使用单引号也没有问题

> 示例代码

```
<div>你好</div>
// 添加src属性 src 表示的就是图片引入的路径
<img src="./1day.md"/>
```

> 本节内容可以参考 https://www.runoob.com/html/html-attributes.html W3C
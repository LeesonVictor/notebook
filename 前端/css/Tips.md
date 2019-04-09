# CSS tips

---

- [CSS tips](#css-tips)
  - [link和import引入CSS的区别](#link和import引入css的区别)
  - [伪类和伪元素](#伪类和伪元素)
    - [1. 伪类](#1-伪类)
    - [2. 伪元素](#2-伪元素)
    - [3.区别](#3区别)

---

## link和import引入CSS的区别

```html
<head>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
```

```css
<style>
    @import url(style.css);
</style>
```

- @import 是 CSS2.1 才出现的概念，所以如果浏览器版本较低，无法正确导入外部样式文件；
- 当 HTML 文件被加载时，link 引用的文件会同时被加载，而 @import 引用的文件则会等页面全部下载完毕再被加载；

## 伪类和伪元素

### 1. 伪类

伪类存在的意义是为了通过选择器，格式化DOM树以外的信息以及不能被常规CSS选择器获取到的信息。
1.格式化DOM树以外的信息。比如： \<a> 标签的:link、:visited 等。这些信息不存在于DOM树中。
2.不能被常规CSS选择器获取到的信息。比如：要获取第一个子元素，我们无法用常规的CSS选择器获取，但可以通过 :first-child 来获取到。

### 2. 伪元素

伪元素可以创建一些文档语言无法创建的虚拟元素。比如：文档语言没有一种机制可以描述元素内容的第一个字母或第一行，但伪元素可以做到(::first-letter、::first-line)。同时，伪元素还可以创建源文档不存在的内容，比如使用 ::before 或  ::after。

### 3.区别

伪类其实是弥补了CSS选择器的不足，用来更方便地获取信息。
而伪元素本质上是创建了一个虚拟容器(元素)，我们可以在其中添加内容或样式。

[https://www.jianshu.com/p/996d021bced3](https://www.jianshu.com/p/996d021bced3)
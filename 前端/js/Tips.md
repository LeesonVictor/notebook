# Tips

标签： 零碎知识点

---

## var 和 let、const的区别

- var最小作用域为函数，let、const最小作用于域为块（大括号）
- 声明在全局的var变量可以通过 `window.变量名` 取到,而let、const则不能通过`window.变量名` 取到。
- var会变量提升(声明提升，赋值不提升)，而let、const不会提升。
- const用于定义不可更改的常量（声明时赋值，后不可重新赋值，但可更改其内部属性的值。变量名全大写）

## querySelectorAll 和 getElementsBy 系列方法的区别

querySelectorAll 的返回值是一个 **静态的** NodeList 对象，
getElementsByClassName、getElementsByTagName返回值是一个 **动态的** HTMLCollection 对象 。getElementById返回一个element。

### 延伸：NodeList和HTMLCollection的区别

- dom结构改变时不会受影响，NodeList不会受影响，HTMLCollection会跟随改变。
- NodeList中包含所有node(包括element、attribute、text等)，HTMLCollection中只包含element。

### node和element的区别

- node包含element、attribute（属性）、text（文本）、comment（注释）、document等
- element是node的一种

[https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType](https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType)
[https://www.cnblogs.com/ron123/p/3764393.html](https://www.cnblogs.com/ron123/p/3764393.html)
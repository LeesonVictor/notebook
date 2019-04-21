# CSS优先级

标签： css 优先级

---

## 直观

1. 行内样式>内联样式=外联样式
2. ID选择器>类选择器=伪类选择器=属性选择器>元素选择器=伪元素选择器>通配符选择器
3. !important申明的优先级最高
4. 就近原则（最晚声明的生效）

## 微观

1. !important权重最高  1,0,0,0,0
2. 行内样式 0,1,0,0,0
3. ID选择器 0,0,1,0,0
4. 类、伪类、属性选择器 0,0,0,1,0
5. 元素、伪元素选择器 0,0,0,0,1

规则：累加不进位。

```css
  a{color: yellow;} /*特殊性值：0,0,0,1*/
  div a{color: green;} /*特殊性值：0,0,0,2*/
  .demo a{color: black;} /*特殊性值：0,0,1,1*/
  .demo input[type="text"]{color: blue;} /*特殊性值：0,0,2,1*/
  .demo *[type="text"]{color: grey;} /*特殊性值：0,0,2,0*/
  #demo a{color: orange;} /*特殊性值：0,1,0,1*/
  div#demo a{color: red;} /*特殊性值：0,1,0,2*/
```

注： 因为就近原则 :link、:visited、:hover、:active,必须按此顺序声明。因为在hover状态时肯定是link状态，在active状态时肯定是link和hover状态

## 参考资料

[https://www.cnblogs.com/wangmeijian/p/4207433.html](https://www.cnblogs.com/wangmeijian/p/4207433.html)
[http://www.runoob.com/w3cnote/css-style-priority.html](http://www.runoob.com/w3cnote/css-style-priority.html)
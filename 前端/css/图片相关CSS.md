# 图片相关CSS

标签： img 

---

[TOC]

---
## object-fit
**作用**：用于调节**img标签长宽**和**图片文件长宽**不匹配时的展示方式。（相当于WPF的Image的Stretch属性）

**取值**：

- fill
- contain
- cover
- none
- scale-down

**浏览器兼容性**：IE不支持

### fill  
描述：将图片铺满整个img标签（相当于WPF中的Fill）
优点：填满。
缺点：会变形（不保证长宽比）
### contain 
描述：保证长的一个方向填满，短的一个方向留白（相当于WPF中的Uniform）
优点：不变形，不裁剪
缺点：填不满，在某一方向有空白
### cover
描述：保证短的一个方向填满，长的一个方向裁剪（相当于WPF中的UniformToFill ）
优点：不变形、不留白
缺点：会裁剪
### none
描述：保证图片本身大小，完全不考虑img的width和height。（相当于WPF中的None）
优点：不缩放、不变形
缺点：可能会留白、可能会裁剪
### scale-down
描述：当img容器比实际图片尺寸大时，相当于none;反之相当于contain。（WPF中没有与之对应）
优点：不变形、不裁剪
缺点：填不满

[https://segmentfault.com/a/1190000011874066](https://segmentfault.com/a/1190000011874066)





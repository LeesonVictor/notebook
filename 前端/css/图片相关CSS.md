# 图片相关CSS

标签： img

---

- [图片相关CSS](#图片相关css)
  - [object-fit](#object-fit)
    - [作用](#作用)
    - [浏览器兼容性](#浏览器兼容性)
    - [取值](#取值)
    - [原理](#原理)
    - [参考资料](#参考资料)

---

## object-fit

### 作用

用于调节 **img标签宽高**和 **图片文件宽高** 不匹配时的展示方式。（相当于WPF的Image的Stretch属性）

### 浏览器兼容性

IE不支持

### 取值

- fill  
描述：将图片铺满整个img标签（相当于WPF中的Fill）。  
优点：填满。  
缺点：会变形（不保证长宽比）。  
- contain  
描述：容器短边（缩小得多，放大得少）填满，长边留白（相当于WPF中的Uniform）。  
优点：不变形，不裁剪。  
缺点：填不满，在某一方向有空白。  
- cover  
描述：容器长边填满，短边裁剪（相当于WPF中的UniformToFill ）。  
优点：不变形、不留白。  
缺点：会裁剪(超出容器不显示)。  
- none  
描述：保证图片本身大小，完全不考虑img的width和height，图片显示在容器中间（相当于WPF中的None）。  
优点：不缩放、不变形。  
缺点：可能会留白、可能会裁剪。  
- scale-down  
描述：当img容器比实际图片尺寸大时，相当于none;反之相当于contain。（WPF中没有与之对应）。  
优点：不变形、不裁剪。  
缺点：填不满。

### 原理

  三个宽高：

- 图片文件本身宽高（w1,h1） 输入
  
- img标签宽高（w2,h2）  输入
  
- 图片最终缩放变形后的宽高（包含超出容器后被裁剪的部分） （w3,h3）  输出
  
1. fill

   ```javascript
   w3 = w2;
   h3 = h2;
   ```

2. contain

   ```javascript
   if(w2/w1 < h2/h1){ //容器宽相对比较短（缩小得多或放大得少）,短边填满，长边按比例缩放
      w3 = w2;
      h3 = (w1/w2)*h1;
   }else{  //容器高相对比较短
      h3 = h2;
      w3 = (h1/h2)*w1;
   }
   ```

   ![图1-1](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/css_imagecss_object_fit.png?raw=true)

3. cover

   ```javascript
   if(w2/w1 < h2/h1){  //容器高相对较长，长边填满。短边按比例缩放(超出容器的居中裁剪)
      h3 = h2;
      w3 = (h1/h2)*w1;
   }else{ //容器宽相对较长
     w3 = w2;
     h3 = (w1/w2)*h1;
   }
   ```

4. none

   ```javascript
   w3 = w1;
   h3 = h1;
   ```

5. scale-down

   ```javascript
   if(w2>w1&&h2>h1){//容器完全容得下图片，相当于none
     ...
   }else{//相当于contain
     ...
   }
   ```

### 参考资料

[https://segmentfault.com/a/1190000011874066](https://segmentfault.com/a/1190000011874066)
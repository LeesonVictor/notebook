# 文本相关CSS

标签: 文本 CSS

---

## 属性

### word-break

- 作用：指定非CJK(中日韩)文本的断行规则。（对中文也会有影响）
- 取值:
  | 值        | 描述                           |
  | --------- | ------------------------------ |
  | normal    | 使用浏览器默认的换行规则。     |
  | break-all | 允许在单词内换行。             |
  | keep-all  | 只能在半角空格或连字符处换行。 |
  - keep-all对英文和normal相同。
  - keep-all会影响中文，导致中文遇到标点符号就换行，没遇到就超出容器。
- 浏览器兼容性：主流浏览器都支持

### overflow-wrap(word-wrap)

- 作用：当word-break不为break-all时，取值break-word可以让一行放不下的单词断行。
- 取值：
  | 值         | 描述                                         |
  | ---------- | -------------------------------------------- |
  | normal     | 只在允许的断字点换行（浏览器保持默认处理）。 |
  | break-word | 在长单词或 URL 地址内部进行换行。            |
- 浏览器兼容性：
  overflow-wrap： 为word-wrap在css3标准中名字。在chrome和opera中支持。微软的浏览器不支持。
  word-wrap： 为微软私有的名字，但基本所有浏览器都支持。

### white-space

- 作用：设置如何处理**元素**内的空白
  1. 不仅仅处理文本空白。也处理div等里面的空白。
  2. 注意空白包括空格和空行。
- 取值：
  | 值                | 描述                                                                                  |
  | ----------------- | ------------------------------------------------------------------------------------- |
  | normal            | 默认。空白会被浏览器忽略。（多个空格保留了一个（要实现多个空格用\&nbsp;），空行删除） |
  | pre               | 空白会被浏览器保留，且不会断行，其行为方式类似 HTML 中的 \<pre> 标签。                |
  | nowrap            | 文本不会断行，文本会在在同一行上继续，直到遇到 \<br> 标签为止。                       |
  | pre-wrap          | 保留空白符序列，但是正常地进行换行。                                                  |
  | pre-line          | 合并空白符序列，但是保留换行符。                                                      |
  | inherit(IE不支持) | 规定应该从父元素继承 white-space 属性的值。                                           |
- 浏览器兼容性：所有浏览器都支持。

### text-overflow

- 作用：规定当文本溢出包含元素时发生的事情。
- 取值：
  | 值                                    | 描述                                 |
  | ------------------------------------- | ------------------------------------ |
  | clip(默认值)                          | 修剪文本                             |
  | ellipsis                              | 显示省略符号来代表被修剪的文本。     |
  | 任意string(只在 Firefox 浏览器下有效) | 使用给定的字符串来代表被修剪的文本。 |

### text-wrap(目前主流浏览器都不支持)

---

## 应用

### 一般断行需求（注意区分断行和换行，断行一行放不下时浏览器自动放到下一行(控制权在浏览器)，换行为使用br标签主动放到下一行（控制权在编码人））

- 中文：按字断行
- 英文(包括数字)：
  1. 按词断行，一个词一行剩余的空间放不下，则空出来放下一行。
  2. 若下一整行也放不下，则放不下的词中的字放下一行（按字断行）

浏览器一般默认实现了中文和英文的1，而在一个词一整行也放不下时，浏览器默认会让文本超出容器显示。
只需加上`overflow-wrap:break-word`即可实现英文2。

### 实现文本不换行，以省略号表示超出的部分

```css
  overflow: hidden;
  white-space: nowrap;<!-不换行 ->
  text-overflow:ellipsis;<!-超出部分显示省略号 ->
```

![https://github.com/LeesonVictor/notebook/blob/master/images/20190415101358.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/20190415101358.png?raw=true)

## 参考资料

- [https://drafts.csswg.org/css-text-3/](https://drafts.csswg.org/css-text-3/)
- [word-break、word-wrap和white-space](https://www.cnblogs.com/yingzi1028/p/6113066.html)
- [彻底搞懂word-break、word-wrap、white-space](https://www.cnblogs.com/dfyg-xiaoxiao/p/9640422.html)
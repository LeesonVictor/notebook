# 《javascript面向对象编程指南》读书笔记

标签： 读书笔记

---

- [《javascript面向对象编程指南》读书笔记](#javascript面向对象编程指南读书笔记)
  - [第一章 面向对象的JavaScript](#第一章-面向对象的javascript)
  - [第二章 基本数据类型与流程控制](#第二章-基本数据类型与流程控制)
    - [变量](#变量)
    - [数据类型](#数据类型)
      - [typeof](#typeof)
      - [数字](#数字)
      - [字符串](#字符串)
        - [转义字符](#转义字符)
      - [bool值](#bool值)
        - [逻辑运算符](#逻辑运算符)
        - [比较运算符](#比较运算符)
      - [undefined与null](#undefined与null)
      - [数组](#数组)
        - [数组元素的增删改查](#数组元素的增删改查)
        - [多维数组](#多维数组)
      - [Map（ES6规范）](#mapes6规范)
      - [Set（ES6规范）](#setes6规范)
    - [流程控制](#流程控制)
      - [条件语句](#条件语句)
      - [循环语句](#循环语句)
  - [第三章 函数](#第三章-函数)

---

## 第一章 面向对象的JavaScript

- HTML专注于内容，CSS专注于表现，JavaScript专注于行为。

- JavaScript术语包含三个部分：

  1. ECMAScript：语言的核心部分（变量、函数、循环等等），独立于浏览器，可以在其他环境中使用。
  2. 文档对象模型（DOM）
  3. 浏览器对象模型（BOM）

- ECMAScript和JavaScript的区别：
  ECMAScript是为了规范各种前端脚本语法的标准（后端node.js也包含ECMAScript），JavaScript只是其的一种实现。

## 第二章 基本数据类型与流程控制

### 变量

- 变量名可以由字母、数字、下划线、**美元符号**组合而成。
- 变量名**不能以数字开头**。
- 变量名区分大小写。

### 数据类型

共6大数据类型

- 值类型
  1. 数字
  2. 字符串
  3. 布尔值
  4. undefined
  5. null

- 引用类型
  6. object

#### typeof

- 作用：查看变量的类型是什么
- 取值：
  1. "number"
  2. "string"
  3. "boolean"
  4. "undefined"
  5. "object"
  6. "function" (相比6种数据类型，null变成了function)

注意：

- `typeof(null) === 'object'; //true`
- 检测变量存在且初始化过用`typeof(somevar) !== "undefined"`

#### 数字

1. 整数：255
2. 浮点数：255.0
3. 八进制数：0377
4. 十六进制数： 0xff
5. 指数：2.55e+2
6. Infinity、-Infinity：超出JavaScript处理范围的数值
7. NaN：表示not a number，`NaN!=NaN;//true`,只能通过isNaN(变量)判断是否为数字，而不能通过`=`。

#### 字符串

1. 字符串+数字=字符串
2. 字符串与数字进行减、乘、除运算=数字

##### 转义字符

|字符串|含义|
|---|---|
|\\\\、\\'、\\"|由于\\、'、"在js中是关键符号，所以需要转义|
|\\n|换行符|
|\\r|回车符|
|\\t|制表符|
|\\u|\\u后面的字符将会被视为Unicode码|

#### bool值

`if(变量)`时，以下值被当作false。

- 空字符串
- null
- undefined
- 数字0
- 数字NaN  

注意：

- 不代表以上值 == false，如`null == false` 返回false
- `if('false')`、`if('0')`都为true，因为非空字符串当作true

##### 逻辑运算符

- 优先级：！> && > || ，但为了可读性，最好加括号。

- 惰性求值：前面的满足，后面不会执行。

##### 比较运算符

|操作符|名称|说明|例子|
|---|---|---|---|---|
|==|相等运算符||`null == undefined;//true`<br>`'1'==true; //true`<br> `'1'==1; //true`|
|===|严格相等运算符|类型相同&&值相同|`null === undefined; //false`<br>`1 === '1'; //false`|
|!=|不相等运算符||`NaN!=NaN;//true`<br>`'1'!=1; //false`|
|!==|严格不相等运算符||`'1'!==1; //true`|
|>|大于运算符||`'2'>1 ;//true`|
|>=|大于等于运算符||`1>='1'; //true`|
|<|小于运算符||`1<'2'; //true`|
|<=|小于等于运算符||`1<='1'; //true`|

注意：
  
- 以上表格仅针对值类型，对于引用类型，若引用的是同一个对象，则相等且严格相等。
- 后四种没有对应的严格大于、严格大于等于、......。

#### undefined与null

- 声明而不初始化一个变量时，javascript会自动用undefined值来初始化。
- 当与数字进行运算时，undefined返回NaN，null则会被当作0进行运算

例子：

```javaScript
 var somevar;
 somevar === undefined;//true
```

```javaScript
 1*undefined;//NaN;
 1*null;//0
```

#### 数组

数组为引用类型，`typeof([]) === 'object' //true`

##### 数组元素的增删改查

- 声明：`let a = [2,4,5]`
- 增加：`a[4]=6;//跳过了a[3]，a[3]将为undefined`
- 删除：`delete a[0];//删除后数组长度不变，被删除地方的值变为undefined`
- 更新：`a[4]=7`
- 访问：`a[0]`

注意：

- delete元素不会改变数组长度，要想改变数组长度见第四章的Array的pop和splice方法。
- 字符串也以当作数组用索引访问每个字符。

##### 多维数组

#### Map（ES6规范）

- 存在必要：JavaScript中的{}的键只能是字符串，若要以其他数据类型(包括引用类型)为键则可以用到map。
- 初始化：
  
  ```javascript

  var m1 = new Map(); // 空Map
  var m2 = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);

  ```

- 操作：
  |属性/方法|作用|
  |---|---|
  |size|返回成员数量|
  |clear()|清空所有成员，无返回值|
  |has(key)|判断是否存在指定成员，返回值为 true / false|
  |get(key)|获取指定成员的值，如不存在则返回 undefined|
  |set(key, value)|为key设置键值，如已经存在该key则更新，否则添加新元素，返回值是实例本身|
  |delete(key)|删除key的键值对，返回值为 true / false|
- 注意：map的键必须唯一，若加入重复的键，后面的值会冲掉前面的值。

#### Set（ES6规范）

- 初始化：
  
  ```javascript

  var s1 = new Set(); // 空Set
  var s2 = new Set([1, 2, 3]); // 含1, 2, 3

  ```

- 操作：
  |属性/方法|作用|
  |---|---|
  |size|返回成员数量|
  |clear()|清空所有成员，无返回值|
  |has(ele)|判断是否存在指定成员，返回值为 true / false|
  |add(ele)|添加元素ele，如果已经存在，没有变动，否则添加，返回值是实例本身|
  |delete(ele)|删除某个值，返回值为 true / false|
- 注意：
  
  1. Set中的值必须唯一，重复的会自动保留一个。（map键、set重复的标准：值类型必须值严格相等，引用类型必须引用同一个对象）
  2. Set没有数组那种通过索引取值的方法，只能够遍历。

### 流程控制

#### 条件语句

- if、if else、if  else if...else
- switch
- 三元表达式

#### 循环语句

- while
- do while
- for
- for in
- for of(es6规范)
- forEach

注意：for in循环遍历键，而for of和forEach会遍历键值。

## 第三章 函数

若函数没有返回值，默认返回undefined。（new 调用构造函数除外）



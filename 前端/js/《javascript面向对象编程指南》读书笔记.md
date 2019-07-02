# 《javascript面向对象编程指南》读书笔记

标签： 读书笔记

---

- [《javascript面向对象编程指南》读书笔记](#javascript面向对象编程指南读书笔记)
  - [第一章 面向对象的JavaScript](#第一章-面向对象的JavaScript)
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
      - [Map（ES6规范）](#MapES6规范)
      - [Set（ES6规范）](#SetES6规范)
    - [流程控制](#流程控制)
      - [条件语句](#条件语句)
      - [循环语句](#循环语句)
  - [第三章 函数](#第三章-函数)
    - [函数定义](#函数定义)
    - [参数](#参数)
    - [返回值](#返回值)
    - [内建函数](#内建函数)
    - [变量作用域](#变量作用域)
    - [变量提升](#变量提升)
    - [匿名函数](#匿名函数)
    - [回调函数](#回调函数)
    - [即时函数（自执行函数）](#即时函数自执行函数)
    - [内部（私有）函数](#内部私有函数)
    - [函数中this指向的坑](#函数中this指向的坑)
    - [返回函数的函数](#返回函数的函数)
    - [能重写自己的函数](#能重写自己的函数)
    - [闭包](#闭包)
      - [作用域链](#作用域链)
      - [写法](#写法)
      - [应用](#应用)
  - [第四章 对象](#第四章-对象)
    - [js中对象与数组的区别](#js中对象与数组的区别)
    - [对象声明和访问](#对象声明和访问)
      - [声明](#声明)
      - [属性的访问](#属性的访问)
      - [属性的增删改](#属性的增删改)
      - [全局对象](#全局对象)
      - [constructor属性](#constructor属性)
      - [instanceof操作符](#instanceof操作符)
      - [对象作为参数传递](#对象作为参数传递)
      - [比较对象](#比较对象)
    - [内建对象](#内建对象)
      - [Object](#Object)
      - [Array](#Array)
        - [length属性](#length属性)
        - [一些内建方法](#一些内建方法)
      - [Function](#Function)
        - [函数对象的内建属性：](#函数对象的内建属性)
        - [call和apply](#call和apply)
      - [Boolean](#Boolean)
      - [Number](#Number)
      - [String](#String)
      - [Math](#Math)
      - [Date](#Date)
      - [RegExp](#RegExp)
        - [replace](#replace)
        - [回调式替换](#回调式替换)
      - [Error对象](#Error对象)
  - [第五章 原型](#第五章-原型)
    - [原型属性](#原型属性)
    - [原型对象上的属性和方法](#原型对象上的属性和方法)
    - [原型链](#原型链)
    - [枚举属性](#枚举属性)
    - [isPrototypeOf()](#isPrototypeOf)
    - [\_\_proto\_\_](#__proto__)
    - [原型作用](#原型作用)
    - [原型陷阱](#原型陷阱)
  - [第六章 继承](#第六章-继承)
    - [实现方法1](#实现方法1)
    - [实现方法2](#实现方法2)
    - [ES6中继承写法](#ES6中继承写法)
  - [第七章 浏览器环境](#第七章-浏览器环境)
    - [BOM（浏览器对象模型）](#BOM浏览器对象模型)
      - [window对象](#window对象)
        - [window.navigator](#windownavigator)
        - [window.location](#windowlocation)
        - [window.history](#windowhistory)
        - [H5中history的API](#H5中history的API)
        - [window.frames](#windowframes)
        - [window.screen](#windowscreen)
        - [window.open/window.close](#windowopenwindowclose)
        - [window.moveTo()、window.moveBy()、window.resizeTo()、window.resizeBy()](#windowmoveTowindowmoveBywindowresizeTowindowresizeBy)
        - [window.alert()、window.confirm()、window.prompt()](#windowalertwindowconfirmwindowprompt)
        - [window.setTimeout()、window.setInterval()](#windowsetTimeoutwindowsetInterval)
        - [window.document](#windowdocument)
    - [DOM(文档对象模型)](#DOM文档对象模型)
      - [DOM节点的访问](#DOM节点的访问)
        - [方法一 索引访问法](#方法一-索引访问法)
        - [方法二 快捷访问法](#方法二-快捷访问法)
      - [DOM节点的修改](#DOM节点的修改)
      - [DOM节点的新建](#DOM节点的新建)
      - [DOM节点的移除](#DOM节点的移除)
      - [只适用于HTML的DOM对象](#只适用于HTML的DOM对象)
    - [事件](#事件)
      - [注册事件三种方式](#注册事件三种方式)
      - [捕捉法和冒泡法](#捕捉法和冒泡法)
      - [阻断冒泡](#阻断冒泡)
      - [防止默认行为](#防止默认行为)
      - [事件类型](#事件类型)
    - [XMLHttpRequest对象](#XMLHttpRequest对象)

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

| 字符串         | 含义                                       |
| -------------- | ------------------------------------------ |
| \\\\、\\'、\\" | 由于\\、'、"在js中是关键符号，所以需要转义 |
| \\n            | 换行符                                     |
| \\r            | 回车符                                     |
| \\t            | 制表符                                     |
| \\u            | \\u后面的字符将会被视为Unicode码           |

#### bool值

`if(变量)`时，以下值被当作false。

- 空字符串
- null
- undefined
- 数字0
- 数字NaN  

注意：

- 不代表以上值 == false，如`null == false; //false`
- `if('false')`、`if('0')`都为true，因为非空字符串当作true

##### 逻辑运算符

- 优先级：！> && > || ，但为了可读性，最好加括号。

- 惰性求值：前面的满足，后面不会执行。

##### 比较运算符

| 操作符 | 名称             | 说明             | 例子                                                                   |
| ------ | ---------------- | ---------------- | ---------------------------------------------------------------------- |  |
| ==     | 相等运算符       |                  | `null == undefined;//true`<br>`'1'==true; //true`<br> `'1'==1; //true` |
| ===    | 严格相等运算符   | 类型相同&&值相同 | `null === undefined; //false`<br>`1 === '1'; //false`                  |
| !=     | 不相等运算符     |                  | `NaN!=NaN;//true`<br>`'1'!=1; //false`                                 |
| !==    | 严格不相等运算符 |                  | `'1'!==1; //true`                                                      |
| >      | 大于运算符       |                  | `'2'>1 ;//true`                                                        |
| >=     | 大于等于运算符   |                  | `1>='1'; //true`                                                       |
| <      | 小于运算符       |                  | `1<'2'; //true`                                                        |
| <=     | 小于等于运算符   |                  | `1<='1'; //true`                                                       |

注意：
  
- 以上表格仅针对值类型，对于引用类型，若引用的是同一个对象，则相等且严格相等。
- 后四种没有对应的严格大于、严格大于等于、......。

#### undefined与null

- 声明而不初始化一个变量时，javascript会自动用undefined值来初始化。
- 当与数字进行运算时，undefined返回NaN，null则会被当作0进行运算

例子：

```javaScript
 let somevar;
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

  let m1 = new Map(); // 空Map
  let m2 = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);

  ```

- 操作：
  | 属性/方法       | 作用                                                                   |
  | --------------- | ---------------------------------------------------------------------- |
  | size            | 返回成员数量                                                           |
  | clear()         | 清空所有成员，无返回值                                                 |
  | has(key)        | 判断是否存在指定成员，返回值为 true / false                            |
  | get(key)        | 获取指定成员的值，如不存在则返回 undefined                             |
  | set(key, value) | 为key设置键值，如已经存在该key则更新，否则添加新元素，返回值是实例本身 |
  | delete(key)     | 删除key的键值对，返回值为 true / false                                 |
- 注意：map的键必须唯一，若加入重复的键，后面的值会冲掉前面的值。

#### Set（ES6规范）

- 初始化：
  
  ```javascript

  let s1 = new Set(); // 空Set
  let s2 = new Set([1, 2, 3]); // 含1, 2, 3

  ```

- 操作：
  | 属性/方法   | 作用                                                            |
  | ----------- | --------------------------------------------------------------- |
  | size        | 返回成员数量                                                    |
  | clear()     | 清空所有成员，无返回值                                          |
  | has(ele)    | 判断是否存在指定成员，返回值为 true / false                     |
  | add(ele)    | 添加元素ele，如果已经存在，没有变动，否则添加，返回值是实例本身 |
  | delete(ele) | 删除某个值，返回值为 true / false                               |
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

### 函数定义

- 声明式定义

  ```javascript
  function func(){} //在全局中，或函数中的函数，多用此法定义
  ```  

- 函数标识记法
  
  ```javascript
      let func = function(){}    //函数当作对象一个属性时，用词定义法,如下：
      let student = {
        name:zhangsan,
        study:function(){
          console.write('study hard!');
        }
      }
  ```

js中函数也是一种数据(应该属于六种数据类型的object，虽说typeof为'function',而不是'object')，故命名规则和变量一样用驼峰，而不是C#中的帕斯卡。

### 参数

- arguments：可以通过索引获取传过来的所有参数,类似数组但不是。
  
  ```javascript

  function foo(x) {
    for (let i=0; i<arguments.length; i++) {
      console.log(arguments[i]);
    }
  }

  ```

- rest(ES6规范)：获取多余的参数。
  
  ```javascript
  function foo(a, b, ...rest) {
    console.log('a = ' + a);
    console.log('b = ' + b);
    console.log(rest);
  }

  foo(1, 2, 3, 4, 5);
  // 结果:
  // a = 1
  // b = 2
  // Array [ 3, 4, 5 ]

  foo(1);
  // 结果:
  // a = 1
  // b = undefined
  // Array []

  ```

### 返回值

- 若函数没有返回值，默认返回undefined。（new 调用构造函数除外）

### 内建函数

- parseInt()
  转换字符串为整数

  ```javascript
  
  parseInt('123abc1');//输出123，遇到第一个字母或其他非法符号截断
  parseInt('FF',16);//输出255，第二个参数为进制
  parseInt('0x377');//输出887，以0x开头代表16进制，无需指定进制
  parseInt('0377');//输出377，虽然以0开头代表八进制，但易与十进制混淆，所以还是当成十进制
  parseInt('1.258e2')；//125
  ```

- parseFloat()
- isNaN()
  判断变量不是数字不能用`a!==NaN`,因为NaN===NaN返回false，所以只能用isNaN判断。
- isFinite()
  表示是否有限，注意Infinity、-Infinity代表正负无限

  ```javascript
  isFinite(Infinity);//false
  isFinite(-Infinity);//false
  isFinite(1e309);//false，因为超出了js能表示的最大数字
  ```

- encodeURI()
  - 存在必要：URL中如`/?&`等都是关键字符，有特殊含义，若需要他们仅仅作为字符出现，则需要'转义'
  - 编码：一般对中文、空格编码，保持 ASCII字母、数字、~!*()@#$&=:/,;?+' 不变。
  - 使用场景：对整个url编码，返回一个完整格式的url。
- decodeURI()
  对应encodeURL的解码。
- encodeURIComponent()
  - 编码：保留 ASCII字母、数字、~!*()'，其他字符编码。
  - 使用场景：对部分url编码，如queryString中一项参数的值也是一个url，则为了转义其中的`/?&`等关键字，需要先用encodeURIComponent编码，再与整个url拼接起来
- encodeURIComponent()
  对应encodeURL的解码。
- escape()、unescape()
  ***已弃用*，用于字符串的编解码，多用于将中文转义成16进制表示  
- eval()
  - 作用：将一段字符串当作js脚本执行。
  - 缺点：
    1. 安全性差
    2. 动态执行代码，效率差
- alert()
  弹窗，且会阻塞js线程。

### 变量作用域

- var声明的作用域为函数体。
- let、const声明的作用域为大括号。
- 函数内不加var、let、const修饰的作用域为全局。不过，要等到**函数被调用后**变量才会创建。
- 全局变量也可以通过`window.变量名`获取到

### 变量提升

- 定义：执行过程进入函数时，函数内变量的**定义**会提升到函数开始处。
- 特点：提升定义，赋值不提升。
- 例子：
  
  ```javascript

  let a = 123;
  function f(){
    alert(a);
    let a = 1;
    alert(a);
  }
  f();
  //输出：先弹出'undefined',再弹出1.
  
  ```

  解释：因为函数域始终优先与全局域，所以全局的123没作用。上面代码被等价的改写为下面

  ```javascript

  let a = 123;
  function f(){
    let a; //变量会被提升至此，且js引擎默认初始化为undefined
    alert(a);
    a = 1; //赋值不会提升，只提升了定义
    alert(a);
  }
  f();

  ```

### 匿名函数

- 一般用来执行一次性的函数，如自执行函数或回调函数
- 一般写成箭头函数形式`()=>{}`。（ES6规范）

### 回调函数

- 函数作为一个参数传递个另一个函数，并在后面这个函数中调用。

### 即时函数（自执行函数）

多用于执行一些一次性的或初始化的任务。

```javascript

function (name){
  alert('Hello'+name+'!');
}('dude'); //匿名自执行函数

```

### 内部（私有）函数

函数内再定义函数。

```javascript

function outer(param) {
  function inner(theinput) {
    return theinput * 2;
  }
  return 'The result is ' + inner(param);
}

```

### 函数中this指向的坑

坑1：

```javascript

let xiaoming = {
    birth: 1990,
    age: function () {//根据出生日期获取xiaoming年龄
        let y = new Date().getFullYear();
        return y - this.birth;
    }
};

let fn = xiaoming.age;//fn指向了age函数，fn跟xiaoming没任何关系
fn();
//输出：Uncaught TypeError: Cannot read property 'birth' of undefined
//原因：相当于window调用的fn，age中的this.birth就是window.birth.
```

坑2：

```javascript

'use strict';

let xiaoming = {
    birth: 1990,
    age: function () {//根据出生日期获取xiaoming年龄
        console.log(this.birth);//这里的this正常的指向xiaoming对象
        function getAgeFromBirth() {
            let y = new Date().getFullYear();
            return y - this.birth;//嵌套函数中的this又指向了window
        }
        return getAgeFromBirth();
    }
};
xiaoming.age();
//输出：Uncaught TypeError: Cannot read property 'birth' of undefined
//原因：对象中的嵌套函数（第二层及以上）中的this指向window，只有直接子级函数的this指向该对象本身。
```

解决办法：

1. 在子级函数中`let that = this;`保存住对象的引用，然后在孙子及更深层嵌套的函数中用`that.属性名`访问对象属性。

  ```javascript

  let xiaoming = {
    birth: 1990,
    getAge: function () {
        let that = this;
        function getAgeFromBirth() {
          let y = new Date().getFullYear();
          return y - that.birth;//that指向了xiaoming
        }
        return getAgeFromBirth();
    }
  };
  xiaoming.getAge();  

  ```

2. 用箭头函数。

  ```javascript

  let xiaoming = {
    birth: 1990,
    getAge: function () {
        let fn = () => new Date().getFullYear() - this.birth; // this指向xiaoming
        return fn();
    }
  };
  xiaoming.getAge();  

  ```

### 返回函数的函数

```javascript

function a(){
  alert('A!');
  return function(){
    alert('B!');
  }
}
let func = a();//弹出'A'
func();//弹出'B'
//或者直接如下
a()();//先弹出'A'，后弹出'B'

```

### 能重写自己的函数

```javascript

  function a() {
    alert('A!');
    a = function(){
      alert('B!');
    };  
  }

  a();//弹出'A!'
  a();//弹出'B!'

```

应用场景：浏览器兼容性探测，初始化时根据浏览器类型，重写某些方法。

### 闭包

#### 作用域链

私有变量可以访问自身作用域（var为函数，let、const为块）和其外层作用域，就形成了一条作用域链。

#### 写法

用一个全局变量指向内层的函数，这样通过这个全局变量就可以访问内层函数同级的变量，突破了作用域链。（看着像从外层访问里层）

1. 函数套函数，返回一个函数

```javascript

let F = function () {
  let b = "local variable";
  let N = function () {
    let c = "inner local";
    return b;
  };
  return N;
};
let inner = F();
inner();//输出"local variable"

```

2. 函数套函数，里层函数赋值给外层变量

```javascript

let inner;
let F = function (){
  let b = "local variable";
  let N = function () {
    return b;
  };
  inner = N;
};
F();
inner();//输出"local variable"

```

函数所绑定的是作用域本身，而不是在函数定义时该作用域中的变量或变量当前所返回的值。
若需要绑定(非引用类型)变量当前值的快照，则可以通过调用传参。因为函数传参是传的当前值的拷贝。

#### 应用

- getter与setter
  通过setter给变量赋值可以加验证。

  ```javascript

  //变量写成局部变量，不可直接访问。通过getter和setter暴露取值和赋值的接口。
  let getValue, setValue;
  (function() {
    let secret = 0;
    getValue = function(){
      return secret;
    };
    setValue = function (v) {
      if (typeof v === "number") {
        secret = v;
      }
    };
  }());


  getValue();//输出0
  setValue(123);
  getValue();//输出123
  setValue(false);//false验证失败，赋值不成功
  getValue();//输出123

  ```

- 迭代器

```javascript

function setup(x) {
  let i = 0;
  return function(){
    return x[i++];
  };
}

let next = setup(['a', 'b', 'c']);
next();//输出"a"
next();//输出"b"
next();//输出"c"

```

## 第四章 对象

### js中对象与数组的区别

|  键类型  | 数据类型 |
| :------: | :------: |
|   数字   |   数组   |
|  字符串  |   对象   |
| 任意类型 |   map    |

在一些程序语言中，通常会存在两种不同的数组形式。

1. 一般性数组，也叫索引型数组或枚举型数组（通常以数字为键名）。
2. 关联型数组，也叫哈希表或者字典（通常以字符串为键名）。

js中数组表示索引型数组，对象表示关联型数组。

### 对象声明和访问

#### 声明

1.文本标识法
  
```javascript

let obj = {
  breed: 'Turtle',
  occupation: 'Ninja'
};

```

对象的属性名若不符合变量命名规范，则属性名需要加引号。

```javascript

let obj = {
  'this':'abc',
  '123':123
}

```

2.构造函数

```javascript

function Hero() {
  this.occupation = 'Ninja';
}
let hero = new Hero();

```

- 构造函数中无需写return，自动返回this。若显式return了一个object,则以显示return的为准。
- 构造函数首字母大写。

#### 属性的访问

1.通过`变量名.属性名`访问

    hero.occupation;

2.通过`变量名[属性名]`访问

    hero['occupation'];

此种访问有两种使用场景：

1. 属性名是一个变量
2. 属性名不符合js变量命名规范

#### 属性的增删改

增：`hero.name = 'zhangsan'`;
改：`hero.name = 'lisi'`;
删：`delete hero.name`;

#### 全局对象

浏览器环境中，全局对象为window。
调用全局变量可以 a 或 window.a 或 this.a 。

#### constructor属性

指向实例化时所用的构造函数。若用文本标识法创建对象，则它的constructor指向Object()。

```javascript

h2.constructor;
//输出
//function Hero(name){
//  this.name = name;  
//}

```

```javascript

let o = {};
o.constructor;
//输出 function Object(){[native code]}

```

#### instanceof操作符

用于判断某个对象是否由某个指定的构造器或其父级构造器所创建。

```javascript

h instanceof Hero;//true
h instanceof Object;//true

```

#### 对象作为参数传递

- 对象类型的以引用类型传递，引用同一份。
- 值类型拷贝一份再传递。

#### 比较对象

当且仅当俩引用指向同一对象时，俩对象相等且严格相等。

```javascript

let fido = {breed: 'dog'};
let benji = {breed: 'dog'};

fido == benji;//输出false

```

### 内建对象

内建对象大致分三类。

1. 数据封装类对象————包括Object、Array、Boolean、Number 和String。
2. 工具类对象————包括Math、Date、RegExp 等用于提供便利的对象。
3. 错误类对象————包括一般性错误对象以及其他各种更特殊的错误类对象。它们可以在某些异常发生时帮助我们纠正程序工作状态。

#### Object

Object是所有对象的父级对象。
`let o = {}`和`let o = new Object()`等价。
Object含以下三个内建属性:

1. o.constructor————返回构造函数的引用。
2. o.toString()————返回对象的描述字符串。
3. o.valueOf()————返回对象的单值描述信息，通常就是对象本身。

#### Array

数组也是一种对象。

```javascript

let a = [];
typeof a;//Object
a instanceof Object;//true

```

相比对象的特殊之处

1. 数组的属性名从0开始递增，并自动生成数值；
2. 数组有一个用于记录元素数量的length属性；
3. 数组在Object上扩展了更多的内建方法。

##### length属性

- length属性会随着数字键名的数量而更新，而忽略非数字键名属性。
  
  ```javascript

    a[0] = 0;
    a.prop = 2;//非数字键名不会增加length
    a.length;//输出1
    a;//输出[0,prop:2];

  ```

- 当手动设置length的值大于数组中元素数量时，剩下的部分会被undefined填充。
- 当手动设置length的值小于数组中的元素数量时，多出的部分元素被移除。

##### 一些内建方法

原素组会改变的方法：

- push————在数组末端添加一个新元素，并返回改变后数组的长度
- pop————移除数组末端的一个元素，返回该元素
- unshift————在数组头部添加若干元素，返回数组长度
- shift————移除数组头部的一个元素，返回该移除的元素
- sort————排序，返回排序后的数组。（原数组也会变）
- reverse————数组元素顺序翻转过来
- indexOf————获取数组中某元素的索引（若为引用类型，必须为同一份引用）
- splice————万能改变数组的方法，截取数组同时填充若干元素，返回截取后的数组。

  ```javascript
  
  let a = [1,3,5,7,9];
  let b = a.splice(1,2,100,101,102);//第二个参数为截取长度，与slice的第二个参数不同
  console.log(a);//[1,100,101,102,7,9]
  console.log(b);//[3,5]

  ```

原数组不受影响，返回一个改变后的数组的方法：

- join————用某个字符串连接数组中的每个元素。（split为把字符串切割成数组）
- slice————截取数组，两参数为截取**起止索引**，包括开始，**不包括结束索引**
- concat————合并两个数组返回

#### Function

##### 函数对象的内建属性：

- constructor————继承自Object（因为js中函数也是一种对象），其引用Function()这个构造函数
- length————记录该函数声明时的参数数量
- prototype
  - 每个函数的prototype属性都指向一个对象
  - 只有在函数是构造函数是才发挥作用
  - 该函数创建的所有对象都会持有一个该prototype 属性的引用，并可以将其当做自身的属性来使用。

##### call和apply

call和apply可以指定方法的执行上下文，从而可以实现一个对象去"借用"另一个对象的方法为己所用。
例如，arguments对象没有数组的内建方法，可以像如下方式调用

```javascript

function f(){
  let args = [].slice.call(arguments);
}

```

通过该方法可以实现**子类对象中调用父类对象中的方法**
例如：Array继承自Object，Array中重写了Object中的toString方法，但在Array中想调用Object中的方法时可以`Object.prototype.toString.call([])`

apply和call的唯一区别是，apply传参放在一个数组里。

#### Boolean

作用：

1. 当作构造函数时，生成一个bool类型的对象（typeof为'object'），一般不这么用，直接用字面量false或true。
2. 当普通函数调用，用于把其他类型的值转换为bool值，且返回的值typeof为boolean。

其他几种基本数据类型也有以上功能

五个基本类型数据都有一个对应的Object类型封装。
`('abcdefg').slice(0,2)`会发生装箱拆箱。
因为slice方法在String类型对象上，所以会先把值类型转换为引用类型，得到结果后再转换回值类型。

#### Number

作用与Boolean相同，但增加了一些属性和方法。

把Number当成一个对象，该对象里有以下属性：

- Number.MAX_VALUE————最大值
- Number.MIN_VALUE————最小值
- Number.POSITIVE_INFINITY————正无穷
- Number.NEGATIVE_INFINITY————负无穷
- Number.NaN————NaN

把Number当成构造函数，该构造函数prototype指向对象上有以下方法：

- toFixed————保留小数位
- toPrecision————把数字格式化为指定的长度
- toExponential————转化位指数写法
- toString————重写了object的toString,有一个可选的radix参数(默认10)
  
  ```javascript

  (255).toString(16);//'ff'

  ```

#### String

- toUpperCase————转大写
- toLowerCasse————转小写
- charAt————返回指定位置的字符，位置不存在时返回空字符串
- indexOf————返回第一个匹配的位置
- lastIndexOf————返回最后一个匹配的位置
- slice————根据起止索引截取部分字符串，不包括截止索引，若截止索引为负值，则相当于与字符串长度相加后的值
- subString————与slice唯一区别是对截止索引为负值时，subString会当作0处理
- split—————根据所传递的分割字符串，将目标字符串分割成一个数组
- concat————连接两个字符串返回

#### Math

Math用法与上面不同，不能new。

常用属性：

- Math.PI————常用数字π
- Math.E————欧拉常数e
- Math.SQRT2————2的平方根
- Math.LN2————2的自然对数
- Math.LN10————10的自然对数

常用方法：

- Math.random————获取0到1之间的某个数
- Math.floor————向下取整
- Math.ceil————向上取整
- Math.round————四舍五入
- Math.max————获取最大值
- Math.min————获取最小值
- Math.pow————指数运算
- Math.sqrt————求平方根
- Math.sin、Math.cos————正弦、余弦

#### Date

用于创建Date对象的构造器函数，可以传递以下几种参数

- 无参数，默认返回当前时间
- 一个用于表现日期的字符串
- 分开传递年、日、月、时间等值
- 一个timestamp值

**注意**：js中的月份是从0开始，0表示一月，1表示二月...

常用方法

```javascript

var now = new Date();
now; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
now.getFullYear(); // 2015, 年份
now.getMonth(); // 5, 月份，注意月份范围是0~11，5表示六月
now.getDate(); // 24, 表示24号
now.getDay(); // 3, 表示星期三
now.getHours(); // 19, 24小时制
now.getMinutes(); // 49, 分钟
now.getSeconds(); // 22, 秒
now.getMilliseconds(); // 875, 毫秒数
now.getTime(); // 1435146562875, 以number形式表示的时间戳

```

同时有相应的set方法设置值。
注意：getDay表示获取星期，getDate才表示获取日

```javascript

Date.now();//返回当前时间的时间戳
Date.parse('Jan 11, 2018');//返回时间戳
Date.UTC(2018,0,11);//返回时间戳

```

#### RegExp

写法：

1. `let re = new RegExp('j.*t','gmi')`
2. `let re = /j.*t/ig`

组成部分：

1. 一个用于匹配的模式文本,如/j.*t/
2. 0或多个修饰符，如i、g、m

修饰符：

- i————ignoreCase,忽略大小写
- g————global,找出所有的匹配
- m————跨行搜索

RegExp对象的方法：

- test————返回一个布尔值
- exec————返回一个匹配到的数组，若加g修饰符，数组可能会有多个元素，不加则最多只有一个

```javascript

/j.*t/.test("Javascript");//false
/j.*t/i.test("Javascript");//true
/j.*t/i.exec("Javascript")[0];//Javascript

```

字符串中使用正则的方法：

- match————返回包含匹配内容的**数组**
- search————返回第一个匹配内容所在**位置**
- replace————将匹配的文本**替换**为指定的字符串
- split————根据指定的正则表达式将字符串**分割**成若干个数组元素

```javascript

let s = 'HelloJavaScriptWorld';
s.match(/a/);//返回["a"],没有加g修饰符，故匹配到第一个就返回
s.match(/a/g);//返回["a","a"],加g后匹配所有
s.search(/j.*a/i);//返回5

```

##### replace

```javascript

s.replace(/[A-z]/,'');//返回elloJavaScriptWorld，替换首个大写字母为空
s.replace(/[A-Z]/g,'')；//返回elloavacriptorld，替换所有大写字母为空
s.replace(/[A-Z]/g,"_$&")；//返回_Hello_Java_Script_World，用$&代替所匹配的文本
s.replace(/([A-Z])/g, "_$1");//返回_Hello_Java_Script_World，若正则表达式中分了组（即带括号），那么可以用$1表示分组中的第一组，$2表示第二组，依此类推

```

**注意**：replace中第一个参数不是正则而是字符串时，只会替换掉第一个。这是与其他语言不同的。

```javascript

"pool".replace('o','*');//返回"p*ol"
"pool".replace('/o/g','*');//返回"p**l"

```

##### 回调式替换

```javascript

function replaceCallback(match){
  return ""+match.toLowerCase();
}

s.replace(/[A-Z]/g,replaceCallback);//输出_hello_java_script_world

```

该回调函数接受一系列参数（以上示例仅用到了第一个参数）

- 首参数是所匹配的内容
- 尾参数是被搜索的字符串
- 倒数第二个参数是匹配内容所在位置
- 剩下的参数是分组所匹配的字符串

#### Error对象

包括一些派生的ReferenceError、RangeError、EvalError、SyntaxError、TypeError、URIError。

Error类对象都有两个属性:

- name————构造当前Error对象的构造器名称
- message————出错的详细信息描述

```javascript

try {
  var total = maybeExists();
  if (total === 0) {
    throw new Error('Division by zero!');
  } else {
    alert(50 / total);
  }
} catch (e){
  alert(e.name + ': ' + e.message);
} finally {
  alert('Finally!');
}

```

IE浏览器跟Chrome、FireFox抛出异常的name和message不同，可以自定义抛出一个匿名对象。

```javascript

throw {
  name: "MyError",
  message: "OMG! Something terrible has happened"
}

```

## 第五章 原型

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%8E%9F%E5%9E%8B.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/%E5%8E%9F%E5%9E%8B.png?raw=true)

js中的继承就是基于原型的。

### 原型属性

函数也是对象，每个函数上都有一个prototype属性。

```javascript

function foo(a,b){
  return a*b;
}

typeof foo.prototype;//输出"object"

```

函数的原型属性只有在函数当作构造函数使用（即使用new调用）时才起作用。

### 原型对象上的属性和方法

- 原型对象上的属性和方法无论实例化多少个对象都只存在一份。
- 如果实例属性名和原型对象上的属性名相同（或方法名相同，因为js中不存在方法重载），则实例属性优先级高。
- 原型对象上的方法也可以通过`this.属性名`访问实例属性值和原型对象上的属性。

### 原型链

每个对象都会有一个构造器，而原型本身也是一个对象，这意味着它必然也有一个构造器，而这个构造器又会有自己的原型。于是这种结构可能会一直不断地持续下去，并最终形成原型链。

### 枚举属性

- 内建对象.propertyIsEnumerable('属性名||方法名||原型链上的属性名||原型链上的方法名')返回false。
- 对象.propertyIsEnumerable('原型链上的属性名||原型链上的方法名')返回false。
- for in 会例举出实例对象和其原型链上的属性或方法。但不会例举内建对象的原型属性。如Object的原型对象的属性和方法。

### isPrototypeOf()

判断一个对象是否是另一个对象的原型对象

```javascript

let monkey = {
  hair:true,
  feeds:'bananas',
  breathes:'air'
};

function Human(name){
  this.name = name;
}
Human.prototype = monkey;

let george = new Human('George');
monkey.isPrototypeOf(george);//返回true

```

获取一个对象的原型对象

```javascript

Object.getPrototypeOf(george);//返回monkey对象
george.constructor.prototype;//这样也可以获取

```

### \_\_proto\_\_

生成一个对象时，js引擎自动在对象上加了一个__proto__属性，指向该对象的原型对象。然后原型对象也是对象，也有一个__proto__属性指向一个原型对象...如此下去，便形成了一条原型链。

\_\_proto\_\_只能在学习或调试环境下使用

注意：以上为对象层面的原型链。new一个对象时，js引擎把构造函数、原型对象层面的链状关系转化为对象层面的原型链。构造原型对象和构造函数之间的链状关系才是我们所需编写的代码。

### 原型作用

1. 实现继承
2. 扩展内建对象

```javascript

//扩展Date，加一个format方法

Date.prototype.format = function (fmt) {
            var o = {
                "M+": this.getMonth() + 1,                 //月份
                "d+": this.getDate(),                    //日
                "h+": this.getHours(),                   //小时
                "m+": this.getMinutes(),                 //分
                "s+": this.getSeconds(),                 //秒
                "q+": Math.floor((this.getMonth() + 3) / 3), //季度
                "S": this.getMilliseconds()             //毫秒
            };
            if (/(y+)/.test(fmt))
                fmt = fmt.replace(RegExp.$1, (this.getFullYear() + "").substr(4 - RegExp.$1.length));
            for (var k in o)
                if (new RegExp("(" + k + ")").test(fmt))
                    fmt = fmt.replace(RegExp.$1, (RegExp.$1.length == 1) ? (o[k]) : (("00" + o[k]).substr(("" + o[k]).length)));
            return fmt;
        };

```

### 原型陷阱

- 对原型对象执行完全替换时，可能会出发原型链中的某种异常。
  1. 在对象生成后才完全替换原型对象。
     此种情况下，先前生成的对象的__proto__还是链接着原先的原型对象。
  2. 完全替换原型对象后生成对象。
     此种情况下，__proto__链接着被替换掉的原型对象。
- prototype.constructor属性是不可靠的。

```javascript

  function Dog(){
    this.tail = true;
  }
  let benji = new Dog();
  Dog.prototype.say = function(){
    return 'Woof!';
  }
  benji.say();//对象生成后，再在原型对象上加方法，依然可以调用该方法
  beiji.constructor === Dog;//返回true

  Dog.prototype = { //此处完全替换掉了原来的原型对象
    paws:4,
    hair:true
  }

  typeof benji.paws;//返回'undefined'

  beiji.say();//返回'Woof!',因为beiji的__proto__属性还链接着原来的原型对象

  let lucy = new Dog();//在完全替换掉原型对象后，再实例化对象
  
  lucy.say();//TypeError:lucy.say is not a function
  lucy.paws;//4
  lucy.constructor;//function Object(){[naticve code]},替换掉原型对象后，该原型对象的constructor属性就不指向Dog了
```

**最佳实践**：当我们重写对象的prototype时，需要重置相应的constructor属性。

## 第六章 继承

js引擎所做的：查找对象属性时，先在对象自身属性中查找，再沿着\_\_proto\_\_链着的对象上查找。
我们所需做的：通过构造函数和原型对象构建链接关系。（new一个对象时，js引擎把转化为通过__proto__把对象之间连接起来）

### 实现方法1

```javascript

Child.prototype = new Parent();
Child.prototype.constructor = Child;//重置原型对象上的constructor属性，不然就指向了Parent

```

缺点：该方法不仅继承了父类的实例属性，还继承了父类的原型属性

### 实现方法2

```javascript

function extend(Child,Parent){
  let F = function(){};
  F.prototype = Parent.prototype;
  Child.prototype = new F();
  Child.prototype.constructor = Child;
}

```

该方法只会继承父类的原型属性，不会继承父类的实例属性。

### ES6中继承写法

ES6中引入了class关键字，但并非js中有了类，只是一个实现继承的语法糖，实际还是通过原型实现继承。

```javascript

class Student {
    constructor(name) {
        this.name = name;//实例属性、方法放在constructor中
    }

    hello() { //原型属性、方法放在外面
        alert('Hello, ' + this.name + '!');
    }
}

class PrimaryStudent extends Student { //extends关键字代表继承自谁
    constructor(name, grade) {
        super(name); // 记得用super调用父类的构造方法!
        this.grade = grade;
    }

    myGrade() {
        alert('I am at grade ' + this.grade);
    }
}

```

## 第七章 浏览器环境

运行javascript代码需要宿主环境，一般是浏览器环境。

### BOM（浏览器对象模型）

BOM（浏览器对象模型）是一个用于访问**浏览器**和**计算机屏幕**的对象集合。可以通过window访问这些对象。

#### window对象

window对象是浏览器中的全局对象，所有的全局变量和函数都可以通过window对象的属性访问。

##### window.navigator

navigator是一个反应浏览器及其功能信息的对象。如navigator.userAgent可以识别不同的浏览器。

##### window.location

location是一个用于存储当前载入页面url信息的对象。

属性：

```javascript

//若果当前页面的url为http://search.phpied.com:8080/search?p=java&what=script#results

for(var i in location) {
  if(typeof location[i] === “string”) {
    console.log(i + ' = "' + location[i] + '"');
  }
}
//输出：
//href = "http://search.phpied.com:8080/search?q=java&what=script#results"
//hash = "#results"
//host = "search.phpied.com:8080"
//hostname = "search.phpied.com"
//pathname = "/search"
//port = "8080"
//protocol = "http:"
//search = "?q=java&what=script"

```

注：location的href中除了hash变化不会引起向服务端发起请求外，其他部分变化都会重新向服务端发起请求。

方法：

- reload()————重新加载当前页面
- assign()————导航到其他页面
- replace()————也是导航到其他页面，但是不会在浏览器的历史记录表中留下记录

##### window.history

window.histoty属性允许我们以有限的权限操作同一个浏览器会话中的已访问页面。

- history.length————查看用户在这之前访问了多少页面
- histoty.forward()————前进
- history.back()————后退
- history.go(-1)————后退一步，同理可以传其他正、负、0数，实现前进、后退、重载当前页面

##### H5中history的API

作用：让无跳转的单站点也可以将它的各个状态保存为浏览器的多条历史记录。当通过历史记录重新加载站点时，站点可以直接加载到对应的状态。

API：

- history.pushState()
  完整是`history.pushState(stateObject, title, url)`，包括三个参数。
  第一个为状态参数，存放需要记录的状态；第二个是标题，目前浏览器忽略它，传空字符串；第三个为当前状态对应的url地址。
- history.repalceState()
  与pushState唯一区别是不会新生成历史记录，而是将当前历史记录替换掉。
- window.onpopstate
  页面前进后退时，若当前url有对应的stateObject则触发事件，并在参数中包含stateObject。

  ```javascript

  //假如当前网页地址为http://example.com/example.html,则运行下述代码后:
  window.onpopstate = function(event) {
    alert("location: " + document.location + ", state: " + JSON.stringify(event.state));
  };
  //绑定事件处理函数
  history.pushState({page: 1}, "title 1", "?page=1");    //添加并激活一个历史记录条目 http://example.com/example.html?page=1,条目索引为1
  history.pushState({page: 2}, "title 2", "?page=2");    //添加并激活一个历史记录条目 http://example.com/example.html?page=2,条目索引为2
  history.replaceState({page: 3}, "title 3", "?page=3"); //修改当前激活的历史记录条目 http://ex..?page=2 变为 http://ex..?page=3,条目索引为3
  history.back(); // 弹出 "location: http://example.com/example.html?page=1, state: {"page":1}"
  history.back(); // 弹出 "location: http://example.com/example.html, state: null
  history.go(2);  // 弹出 "location: http://example.com/example.html?page=3, state: {"page":3}

  ```

##### window.frames

window.frames属性是当前页面中所有框架的集合。
frames中的每个元素都包含了一个页面，都有各自的window全局对象。

##### window.screen

screen所提供的是浏览器以外的环境信息。

- screen.colorDepth————当前显示器的色位
- screen.width————屏幕宽
- screen.height————屏幕高
- screen.availWith————屏幕可用宽（与width不同之处是availWith不包括任务栏）
- screen.availHeight————屏幕可用高（不包括任务栏）

##### window.open/window.close

打开窗口、关闭窗口

##### window.moveTo()、window.moveBy()、window.resizeTo()、window.resizeBy()

**注**：Chrome、edge中测试均无反应，已废弃。

##### window.alert()、window.confirm()、window.prompt()

- window.alert()————弹出提示框
- window.confirm()————弹出确定框，可以选择确定或取消，相应返回true或false
- window.prompt()————弹出带输入框的窗口，输入后点确定，返回所输入的文本

##### window.setTimeout()、window.setInterval()

setTimeout:在一定时间后执行

```javascript

function boo(){
  console.log('boo!');
}

let id = setTimeout(boo,2000);//2秒后执行boo方法
clearTimeout(id);//根据id取消计时器

```

setInterval:每隔多少毫秒执行一次

```javascript

let id = setInterval(boo,2000);//每隔2秒执行一次
clearInterval(id);//根据id取消计时器

```

##### window.document

### DOM(文档对象模型)

DOM是一种将XML或HTML文档解析成树形节点的方法。通过DOM的方法与属性，我们可以访问到页面中的任何元素，并进行元素的修改删除及添加操作。

基于DOM Level1用于解析所有XML文档的那部分称为Core DOM,在Core DOM上进行扩展的那部分称为HTML DOM。

![https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/Core&HTML_DOM.png?raw=true](https://github.com/LeesonVictor/notebook/blob/master/images/%E5%9B%BE%E7%89%87/Core&HTML_DOM.png?raw=true)

#### DOM节点的访问

##### 方法一 索引访问法

- nodeType————节点类型，常用的1（元素）、2（属性）、3（文本）...
- nodeName————节点名称，对HTML标签来说，一般就是标签名（即tagName属性），对文本则是#text
- nodeValue————节点值，对文本节点来说，值就是实际文本。

document表示当前所访问的文档。
document.documentElement表示document上的HTML节点。

document.documentElement（即HTML节点）有三个，即head元素、body元素，以及两者之间的空白（空白默认为文本节点）。

- 节点相关：
  - hasChildNodes()————判断某节点是否包含子节点
  - childNodes————NodeList类型的子节点集合,通过索引可以访问到子节点
  - parentNode————某节点的父节点
- 属性相关：
  - hasAttributes()————检查元素是否存在属性
  - attributes————属性集合，通过索引访问
  - getAttribute()————获取对应属性名的值
  - 直接在节点后面.属性名，如`节点对象.id`访问id属性的值，`节点对象.className`访问class属性的值
- 节点中的内容相关：
  - textContent————节点中的文本
  - innerHTML————节点中的html的字符串

若一段HTML结构如下：

```HTML

<html>
  <head></head>
  <!--这中间虽然什么都没有，但其实还是有一个text节点-->
  <body>
    <p class="opener">first paragraph</p>
    <p><em>second</em> paragraph</p>
    <p id="closer">final</p>
    <!-- and that's about it -->
  </body>
</html>

```

```javascript

document.documentElement.childNodes[1];//#text，因为head和body之间存在一个空白，该空白为text节点
document.documentElement.childNodes[1].parentNode;//<html>...</html>
let bd = document.documentElement.childNodes[2];
bd.childNodes.length;//9,因为四个节点（包括注释）之间、子节点和父节点之间一共存在5个空白的text节点，所以一共9个节点

bd.childNodes[1].hasAttributes();//true，第一个标签有个class属性。注意索引0是空白text，索引1才是p标签
bd.childNodes[1].attributes.length;//1
bd.childNodes[1].attributes[0].nodeName;//'class'
bd.childNodes[1].attributes[0].nodeValue;//'opener'
bd.childNodes[1].attributes['class'].nodeValue;//'opener'
bd.childNodes[1].getAttribute('class');//'opener'
bd.childNodes[1].className;//'opener'
bd.childNodes[1].nodeName;//'p'
bd.childNodes[1].textContent;//'first paragraph'
bd.childNodes[1].innerHTML;//'first paragraph'
bd.childNodes[3].textContent;//'second paragraph'
bd.childNodes[3].innerHTML;//'<em>second</em> paragraph'
bd.childNodes[1].childNodes[0].nodeValue;//'first paragraph'

```

##### 方法二 快捷访问法

索引法的问题：

- 访问的节点层次很深时，需要写很长的代码
- 节点之间存在空白text节点，导致计算索引很麻烦

快捷方法：

- getElement系列：
  - getElementsByTagName()————以标签名为参数，返回当前html页面中所有匹配该标签名的元素集合
  - getElementsByClassName()————以类名为参数，返回所有该类名的元素集合
  - getElementById()————以id为参数返回一个element
  - getElementsByName()————以name属性为参数，返回所有该name属性的元素集合
- querySelector系列
  - querySlector()————通过css选择器返回第一个元素
  - querySelectorAll————通过css先选择器返回所有元素

注：getElement系列除了getElementById返回一个Element外，其他都返回一个HTMLCollection集合，HTMLCollection是动态的，会随着文档树的变化动态更新。
querySelector系列返回一个NodeList，NodeList是静态的，获取后，文档树变化不会影响NodeList.

```javascript

document.getElementsByTagName('p').length;//3
document.getElementsByTagName('p')[0];//<p class="opener">first paragraph</p>
document.getElementsByTagName('p')[0].className;//'opener'
document.querySlector('p').className;//'opener'
document.querySlectorAll('p')[0].className;//'opener'

```

body虽然说嵌套在html标签里，但document.body就可以访问到body，而不用document.documentElement.body。

- nextSibling————下一个相邻节点
- previousSibling————上一个相邻节点
- firstChild————第一个子节点，一般为空白text
- lastChild————最后一个子节点，一般为空白text

#### DOM节点的修改

- innerHTML————修改元素里的HTML
- nodeValue————修改元素的内容，text类型元素则为文本值
- style————修改元素的样式

```javascript

let my = document.getElementById(,'closer');
my.innerHTML = 'final!!!';
my.innerHTML = '<em>my</em> final';
my.firstChild;//<em>my</em>
my.firstChild.firstChild;//'my'
my.firstChild.firstChild.nodeValue = 'your';

my.style.border = '1px solid red';
my.style.cssText += 'font-weight:bold;';//直接在原有cssText属性上加css字符串文本

```

#### DOM节点的新建

- createElement()————新建元素
- createTextNode()————新建文本节点
- cloneNode()————拷贝节点，参数传false则为浅拷贝，传true则为深拷贝
- appendChild()————添加到最后
- insertBefore()————插入到某元素前面
- replaceChild()————替换某元素

注意：后三个方法调用方是父容器节点。

```javascript

let p = document.createElement('p');
p.innerHTML = '<em>yet</em> another';
p.style.border = '2px dotted blue';
document.body.appendChild(p);
let list=document.getElementById("myList")
list.insertBefore(p,list.childNodes[0]);//第一个参数为新节点，第二个参数为插入谁的前面

item.replaceChild(p,list.childNodes[0]);//第一个参数为替换者，第二个为被替换者

document.body.appendChild(p.cloneNode(false));//将只会拷贝一个p标签，相当于document.body.appendChild(document.createElement('p'));
document.body.appendChild(p.cloneNode(true));//p及p标签里的子元素都将拷贝

```

#### DOM节点的移除

- removeChild()————移除节点
- replaceChild()————替换节点
- innerHTML='' ————把innerHTML置为空字符串

```javascript

let p = document.getElementsByTagName('p')[1];
let removed = document.body.removeChild(p);

let p1 = document.getElementsByTagName('p')[1];
let replaced = document.body.replaceChild(removed,p1);

document.body.innerHTML = '';//清空body里的所有HTML

```

#### 只适用于HTML的DOM对象

以上总结的都是属于DOM Level 0(或叫Core DOM)，既适用于XML又适用于HTML。以下的只适用于HTML。

- document.body————HTML中的body元素
- document.images————当前页中所有图片的集合，等价于Core DOM中的document.getElementsByTagName('img')
- document.links————包含所有`<a href='...'/>`的集合
- document.anchors—————包含所有`<a name='...'>`的集合
- document.forms————包含所有表单的集合

- document.write()————在页面载入时插入一些HTML元素，当载入完成后调用则会覆盖整个HTML。一般没什么用。

- document.cookie————获取或设置cookie
- document.title————获取或设置title
- document.referrer————记录前面访问的页面的URL，同HTTP 头信息中的Referer
- document.domain————获取或设置当前域名，注意设置只能比真实域名更简短，如www.yahoo.com改为yahoo.com
- document.location————同window.location

### 事件

#### 注册事件三种方式

1.内联HTML属性法

```html

<div onclick="alert('Ouch!')">click me</div>

```

缺点：Javascript代码和HTML耦合在一起。

2.元素属性法

```html

<div id="my-div">click</div>

```

```javascript

let myelement = document.getElementById('my-div');
myelement.onclick = function() {
alert('Ouch!');
}

```

缺点：只能指定一个事件函数。

3.事件监听器法

```html

<p id="closer">final</p>

```

```javascript

let mypara = document.getElementById('closer');
mypara.addEventListener('click', function(){alert('Boo!')}, false);
mypara.addEventListener('click', console.log.bind(console), false);

```

移除某个监听器：

```javascript

function func(){
  alert('Woo');
}
mypara.addEventListener('click', func, false);
mypara.removeEventListener('click', func, false);

```

注意：移除某个监听器时，传递的方法参数必须是同一个方法的引用，即使写一个完全相同的方法爷不行。故需要移除的监听器在注册时不能用匿名方法。

#### 捕捉法和冒泡法

addEventListner方法的第三个参数，当置为true时为捕捉法，默认为false即冒泡法。

```html

<body>
  <ul>
    <li><a href="http://phpied.com">my blog</a></li>
  </ul>
</body>

```

单击链接

- 事件捕捉————单机首先发生在document上，然后依次传递给body、列表、列表项，并最终到达该链接，称为捕捉法。
- 事件冒泡————单机首先发生在链接上，然后逐层向上冒泡，直到document对象，称为冒泡法

按照DOM2的规定，事件传播分三阶段：先捕捉标签，然后到达标签，再冒泡。

#### 阻断冒泡

在最里层的处理器中加`e.stopPropagation()`，就不会触发上层父容器的事件。

```javascript

function paraHandler(e){
alert('clicked paragraph');
e.stopPropagation();
}

```

#### 防止默认行为

在浏览器中某些元素的事件有一些预定义行为，例如，单机链接会载入另一个页面。可以在事件处理器中加`e.preventDefault()`来阻断默认行为。

```javascript

// 在点击所有链接前询问是否导航至目标链接，若选择否，则不导航
let all_links = document.getElementsByTagName('a');
for (let i = 0; i < all_links.length; i++) {
  all_links[i].addEventListener(
    'click',
    function(e){
      if (!confirm('Are you sure you want to follow this link?')){
        e.preventDefault();
      }
    },
    false // don't use capturing
  );
}

```

#### 事件类型

- 鼠标类事件
  - 鼠标键的按下、松开、单击、双击
  - 鼠标的悬停、移出、拖动
- 键盘类事件
  - 键盘键的按下、输入、松开
- 载入/窗口类事件
  - 载入（图片、页面或其他组件完成载入操作）、卸载（指用户离开当前页面）、卸载之前（由脚本提供的、允许用户终止卸载的选项）
  - 中止（指用户在IE 中停止页面或图片载入）、错误（指在IE 发生了JavaScript错误或图片载入失败）。
  - 调整大小（指浏览器窗口大小被重置）、滚动（指页面进行了滚动操作）、上下文菜单（即右键菜单出现）。
- 表单类事件
  - 获得焦点（指某字段获得输入）、失去焦点（指离开该字段）。
  - 改变（指改变某字段的值后离开）、选中（指某文本字段中的文本被选中）。
  - 重置（指擦除用户输入的所有信息）、提交（指发送表单）。

现代浏览器还有dragstart、dragend、drop事件，触控设备还有touchstart、touchmove、touchend事件。

### XMLHttpRequest对象

```javascript

let xhr = new XMLHttpRequest();
xhr.onreadystatechange = myCallback;
xhr.open('GET','somefile.text',true);
xhr.send('');//若要携带参数则以格式'key=value&key2=value2'

fuction myCallback(){
  if(xhr.readyState<4){
    return;
  }
  if(xhr.status!==200){
    alert('Error!');
    return;
  }
  alert(xhr.responseText);
}

```

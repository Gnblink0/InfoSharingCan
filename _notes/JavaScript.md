---
---

课程：[黑马程序员 零基础JavaScript入门 - bilibili](https://www.bilibili.com/video/BV1ux411d75J)

⚠️ 以下直接复制粘贴ob里的笔记，未做格式化处理，包括一些无法识别的标题链接和内链图片

# 是什么
[什么是 JavaScript？ - 学习 Web 开发 | MDN](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/What_is_JavaScript)

前端中的编程语言 %%html 和 css 都不能算作编程语言%%

- 特点
	- JavaScript 是一种轻量级的编程语言。
	- JavaScript 是可插入 HTML 页面的编程代码。


# 黑马
## 前言
### 历史
布兰登·艾奇 (Brendan Eich, 1961 年~）
神奇的大哥在1995年利用10天完成 JavaScript 设计
网景公司最初命名为 Livescript，后来在与 Sun 合作之后将其改名为JavaScript
- JavaScript 与 Java %%雷锋和雷峰塔的关系XD%%
	- JavaScript 与 Java 是两种完全不同的语言，无论在概念上还是设计上。
	- Java（由 Sun 发明）是更复杂的编程语言。
	- JavaScript 由 Brendan Eich 发明。它于 1995 年出现在 Netscape 中（该浏览器已停止更新），并于 1997 年被 ECMA（一个标准协会）采纳。ECMA-262 是 JavaScript 标准的官方名称。

### 是什么？
是一种运行在客户端的脚本语言（ Script 是脚本的意思）

脚本语言：不需要编译，运行过程中由 [[#浏览器执行 JS 简介|js 解释器（js 引擎）]]逐行来进行解释并执行

现在也可以基于 Nodejs 技术进行服务器端编程


### 用处
- 表单动态校验（密码强度检测）%%你不能输如一个错误密码就传到后端服务器去验证啊，那样后端压力太大了 %%（JS 产生最初的目的%%太强了 后面一不小心就揽了太多活%%）
- 网页特效
- 服务端开发(Node.js)
- 桌面程序([[Electron]])
- App(Cordova)
- 控制硬件-物联网(Ruff)
- 游戏开发(cocos2d-js)


### 浏览器执行 JS 简介
- [[浏览器]]分成两部分：渲染引擎和JS引擎
	- 渲染引擎：用来解折HTML 与CSS，俗称内孩，比如chrome 浏览器的 blink，老板本的webkt
	- JS引擎：也称为JS解释器。用来读取网页中的JavaScript代码，对其处理后运行，比如 chrome 浏览器的 V8

浏览器本身并不会执行 JS 代码，而是通过内置 JavaScript 引擎 (解释器) 来执行 JS 代码。JS 引擎执行代码时逐行解释

每一句源码（转换为机器语言），然后由计算机去执行，所以 JavaScript 语言归为**脚本语言**，会逐行解释执行。

%%翻译一句，执行一句%%

当浏览器执行到一段 JavaScript 代码时，通常会按从上往下的顺序执行这段代码。这意味着你需要注意代码书写的顺序。

JavaScript 是轻量级解释型语言。浏览器接受到 JavaScript 代码，并以代码自身的文本格式运行它。技术上，几乎所有 JavaScript 转换器都运用了一种叫做即时编译（just-in-time compiling）的技术；当 JavaScript 源代码被执行时，它会被编译成二进制的格式，使代码运行速度更快。尽管如此，JavaScript 仍然是一门解释型语言，因为编译过程发生在代码运行中，而非之前。


### JS 的组成

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220707094153.png)

ECMAscript：js代码
DOM、BOM：js[[API]]

#### ECMAScript
ECMAScript 是由 ECMA 国际（原欧洲计算机制造商协会）进行标准化的一门编程语言，这种语言在万维网上应用广泛，它往往被称为 JavaScript 或 JScript，但实际上后两者是 ECMAScript 语言的实现和扩展。
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220707094352.png)
%%哈哈哈微软公司不要脸……%%

ECMAScript: ECMAScript 规定了**JS的编程语法和基础核心知识**，是所有浏览器厂商共同遵守的一套JS语法工业标准。

#### DOM—文档对象模型
文档对象模型(Document Object Model ，简称DOM），是W3C组织推荐的处理可扩展标记语言的标准编程接口。
通过 DOM提供的接口可以对页面上的各种元素进行操作（大小、位置、颜色等）。

#### BOM—浏览器对象模型
BOM (Browser Object Model，简称 BOM) 是指浏览器对象模型，它提供了独立于内容的、可以与浏览器窗口进行互动的对象结构。
通过BOM可以操作浏览器窗口，比如弹出框、控制览器跳转、获取分辦率等。

### 书写位置
JS 有 3 种书写位置，分别为行内、内嵌和外部。

#### 行内式
行内式：直接写在 html 标签内
`＜input type="button" value="点我试试" onclick="alert ('Hello World' )" />`
- 可以将单行或少量JS代码写在HTML标签的事件属性中（以on 开头的属性），如：onclick
- 注意单双引号的使用：在HTML中我们推荐使用双引号,JS 中我们推荐使用单引号
- 可读性差，在html中编写JS大量代码时，不方便阅读；
- 引号易错，引号多层嵌套匹配时，非常容易弄混；
- 特殊情况下使用

#### 内嵌式
内嵌式：写在 html `head` 里，`<SCRIPt> </SCRIPt>`
```
<script>
alert ( 'Hello World~!")；
</script>
```
• 可以将多行 JS 代码写到 `<script> `标签中
- 内嵌 JS 是学习时常用的方式

#### 外部JS文件
外部式： `<script src="my.js"></script〉`
- 利于HTML页面代码结构化，把大段JS代码独立到HTML页面之外，既美观，也方便文件级别的复用
- 这是一个双标签，但是引用外部 JS文件的 script 标签**中间不可以写代码**
- 适合于JS代码量比较大的情况



### （注释）
- in-line comment  
`// This is an in-line comment.` 

- multi-line comment: 
```js
/* This is a
multi-line comment */
```



### JavaScript输入输出语句

为了方便信息的输入输出，JS中提供了一些输入输出语句，其常用的语句如下： 
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220707104032.png)
prompt 输入 让用户输入
alert 输出 展示给用户
console 控制台输出 给程序员测试

## 变量（Variables）
- [[#变量概述|变量概述]]（能够说出变量的主要作用）
- [[#变量的使用|变量的使用]]（能够写出变量的初始化）
- [[#变量语法扩展|变量语法扩展]]（能够说出变量的命名规范）
- [[#变量命名规范|变量命名规范]]
- [[#交换变量案例|交换变量案例]]（能够画出变量是如何在内存中存储的、能够写出交换变量案例）



### 变量概述
[如何存储你需要的信息 — 变量 - 学习 Web 开发 | MDN](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Variables)

 1.1 什么是变量
白话：变量就是一个装东西的盒子。
通俗：变量是用于存放数据的容器。我们通过变量名 获取数据，甚至数据可以修改。
本质：变量是程序在**内存**中申请的一块用来存放数据的**空间**。
变量由两部分组成 %%比喻：酒店订房%%
	空间
	命名

### 变量的使用
变量在使用时分为两步：1.声明变量%%告诉前台我要订房%% 2. 赋值 %%住进去%%

#### 声明变量

- 三种声明方法
	- var 全局 被淘汰
	- let 局部 现在使用得最多的
	- const 只读（常量） 不能更改数据

`var age; // 声明一个名称为age的变量`
- var 是一个JS关键字，用来声明变量(variable变量的意思）。使用该关键字声明变量后，计算机会自动为变量分配内存空间，不需要程序员管
- age 是程序员定义的变量名，我们要通过变量名来访问内存中分配的空间

![[JavaScript#^dsf0dq]]


🌟 我们建议您在代码中尽可能多地使用 `let`，而不是 `var` 

- 集体声明的正确格式
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220818233714.png)
不能盲目连写，后面的直接赋值没有声明

#### 赋值
`age=10; //给 age 这个变量赋值为10`

记住：把右边给左边

#### 变量的初始化
声明一个变量并赋值，我们称之为**变量的初始化**。
`var age=18; //声明变量同时赋值为18`

#### 案例
``` javascript
let userName = prompt('请输入你的名字');
alert(userName);
// 给变量赋值为用户输入的数据
```


### 变量语法扩展
#### 更新变量
一个变量被重新复赋值后，它原有的值就会被覆盖，变量值将以最后一次赋的值为准。
var会被覆盖，let不会

##### let
我们建议您在代码中尽可能多地使用 `let`，而不是 `var` ，因为没有理由使用 `var`（历史原因）

One of the biggest problems with declaring variables with the `var` keyword is that you can easily ==overwrite== variable declarations:

```js
var camper = "James";
var camper = "David";
console.log(camper);
```

In the code above, the `camper` variable is originally declared as `James`, and is then overridden to be `David`. The console then displays the string `David`.

In a small application, you might not run into this type of problem. But as your codebase becomes larger, you might accidentally overwrite a variable that you did not intend to. ==Because this behavior does not throw an error, searching for and fixing bugs becomes more difficult.==

==A keyword called `let` was introduced in ES6, a major update to JavaScript==, to solve this potential issue with the `var` keyword. You'll learn about other ES6 features in later challenges.

If you replace `var` with `let` in the code above, it results in an error:

```js
let camper = "James";
let camper = "David";
```

The error can be seen in your browser console.
So unlike `var`, when you use `let`, a variable with the same name can only be declared once.



#### 同时声明多个变量
同时声明多个变量时，只需要写一个 var，多个变量名之间使用英文逗号隔开。

```
var age=10, name ="zs", sex = 2；
```

#### 声明变量的特殊情况
![[Pasted image 20220707114411.png]]
%%不声明只赋值居然可以使用，c语言大震惊，python表示我也可以，我甚至根本不用声明%%


### 变量命名规范
- 由字母(A-Za-z）、数字(0-9)、下划线(`_`)、美元符号(＄)組成%%只能用这两个符号，不能用其他的，不能用空格%%
- 严格区分大小写。varapp;和 varApp;是两个变量
- 不能 以数字开头。18age 是错误的
- 不能 是关键字、保留字。例如：var、 for、 while
	- 错了会有波浪线提醒你
	- name不是关键字和保留字，但是在很多浏览器里有特殊含义，也不要使用
- 变量名必须有意义。用英文单词写，不要写拼音首字母简写 %%我写的变量你来猜 ❌%%
- 遵守[[变量命名规范|驼峰命名法]]。首字母小写，后面单词的首字母需要大写。myFirstName
- 推荐翻译网站：有道 爱词霸


### 交换变量案例
js是编程语言，有很强的逻辑性在里面：写代码之前可以先用中文梳理一下逻辑，实现这个要求的思路 先怎么做后怎么做

交换两个变量的值（乾坤大挪移）：运用一个临时变量充当“桌子”

``` js
	let temp;
	let apple1 = '青苹果';
	let apple2 = '红苹果';

	temp = apple1;
	apple1 = apple2;
	apple2 = temp;

	console.log(apple1);
	console.log(apple2);
```

## 数据类型
能够说出5种简单数据类型
能够使用 typeof获取变量的类型
能够说出1~2种转换为数值型的方法
能够说出1~2种转换为字符型的方法
能够说出什么是隐式转换

- [[#数据类型简介|数据类型简介]]
- [[#简单数据类型|简单数据类型]]
- [[#获取变量数据类型|获取变量数据类型]]
- [[#数据类型转换|数据类型转换]]


### 数据类型简介
#### 为什么需要数据类型
在计算机中，不同的数据所需占用的存储空间是不同的，为了便于把数据分成所需内存大小不同的数据，充分利用存储空间，于是定义了不同的数据类型。%%胖的人要睡双人床 %%

#### 变量的数据类型
变量是用来存储值的所在处，它们有名字和数据类型。变量的数据类型决定了如何将代表这些值的位存储到计算机的内存中。

JavaScript 是一种弱类型或者说动态语言。这意味着js不同于其他一些语言(如C、JAVA)，它不用提前声明变量的类型。js的变量数据类型是 只有程序在运行过程中，根据等号右边的值来确定的。 ^dsf0dq

JavaScript 拥有动态类型，同时也意味着相同的变量可用作不同的类型：
[[JavaScript#更新变量]]后，数据类型也会随之改变

### 数据类型的分类
js一共有8个变量数据类型：`undefined`, `null`, `boolean`, `string`, `symbol`, `bigint`, `number`,  `object`.

- 基本类型
	- `undefined`
	- `null`
	- `boolean` 
	-  `string`
	-  `number`
	- `symbol`
	- `bigint`
	-  `object` [[#对象]]


JS把数据类型分为两类：
	简单数据类型（五个：Number, String, Boolean, Undefined, Null)
	复杂数据类型 ( object)

![[Pasted image 20220707121212.png]]
#### 数字型 number
JavaScript 数字类型既可以用来保存整数值，也可以保存小数 (浮点数）。

##### 数字型进制
最常见的进制有二进制、八进制、十进制、十六进制。
输出时会默认转换成十进制

- 八进制
数字序列范围：0~7
程序里面数字前面加 0 表示八进制

```
var num1 = 07;
// 对应十进制的7
var num2 =010;
//对应十进制的8
var num3 = 012;
// 对应十进制的10
```

- 十六进制
数字序列范围：0~9 以及 A~F
数字的前面加 0x 表示十六进制

`var num = OXA;`

##### 数字型范围
JavaScript 中数值的最大和最小值
```
alert (Number.MAX VALUB); // 1.7976931348623157e+308
alert (Number.MIN VALUE);// 5e-324
```

##### 数字型三个特殊值
- Infinity，代表无穷大，大于任何数值
- -Infinity，代表无穷小，小于任何数值
- NaN, Not a number，代表一个非数值

```
alert (Infinity); // Infinity
alert (-Infinity); // -Infinity
alert (NaN) // NaN
```


isNaN (） 
这个方法用来判断非数字  并且返回一个值 如果是数字返回的是 false 如果不是数字返回的是 true
`console. 1og(isNaN(12))；` 返回结果 false

使用场景：验证表单的数据，你不知道用户输入的是什么，所以这个很实用

#### 字符串型 String
字符串型可以是引号中的任意文本，其语法为"双引号"和'单引号'
因为 HTML标签里面的属性使用的是双引号，JS这里我们更推荐使用单引号。

1. 字符串引号嵌套
JS 可以用单引号嵌套双引号，或者用双引号嵌套单引号（外双内单，外单内双）

2. 字符串转义符
类似HTML里的特殊字符，字符串中也有特殊字符，我们称之为转义符，
转义符都是`\`开头的


3. 字符串长度
字符串是由若干字符组成的，这些字符的数量就是字符串的长度。通过字符串的length属性可以获取整个字符串的长度。
`console. 1og(str. length)；`
 ^jr4ek3

4. 字符串拼接
多个字符串之间可以使用 +进行拼接，其拼接方式为字符串 任何类型=拼接之后的新字符串
`console. log ('我是' + '关念')；`

+号总结口诀：数值相加，字符相连
	只要拼接里有字符串，结果一定是字符串
	但是注意 如果是两个数字 没有字符串 结果是数字

变量和字符串相连的口诀：引引加加%%哈哈哈其实并不能少写 只是方便打字了 我还以为能像 css 那样连写%%


布尔型 Boolean
布尔类型有两个值：true和 false，其中 true 表示真（对），而false 表示假（错）。
布尔型和数字型相加的时候，true 的值为1 ，false 的值为 0。


一个声明后没有被赋值的变量会有一个默认值 undefined (如果进行相连或者相加时，注意结果）
一个声明变量给 null 值，里面存的值为空（学习对象时，我们继续研究 nul)

``` js
var variable;
console. log (undefined)；// unde fined
console.log('你好'，+ undefined); // 你好undefined
console.log (11 + undefined)； // NaN
console. log (true + undefined)； // NaN
```


``` js
var vari = null;
console.1og("你好"，+ vari); //你好null
console. log(11 + vari); // 11
console.1og (true + vari); // 1
```

### 获取变量数据类型 

typeof 可用来获取检测变量的数据类型

``` js
var num = 10；
console.log(typeof num)；
```

```js
// prompt 娶过来的值是 字符型的
var age
prompt（' 请输入您的年龄"）；
console. 1og(age)；
console. 1og(typeof age)；
```


还可以通过控制台颜色来**判断**
字符串-黑色


3.2 字面量（literal）
字面量是在源代码中一个固定值的表示法，通俗来说，就是字面量表示如何表达这个值。%%一眼看过去就知道 看到数字就知道是数字 看到引号就知道是string%%
数字字面量：8,9,10
字符串字面量：‘黑马程序员，"大前端"
布尔字面量：true, false ^31bb98


### 数据类型转换
使用表单、prompt 获取过来的数据默认是字符串类型的%%即用户输入的数字是字符串%%，此时就不能直接简单的进行加法运算，而需要转换变量的数据类型。通俗来说，就是<font color=#F36208>把一种数据类型的变量转换成另外一种数据类型</font>。

我们通常会实现3种方式的转换：
	转换为字符串类型
	转换为数字型（重点）
	转换为布尔型

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220708014937.png)

#### 转换为字符串
![[Pasted image 20220807123458.png]]
toString()和 String() 使用方式不一样。
三种转换方式，我们更喜欢用第三种加号拼接字符串转换方式，这一种方式也称之为隐式转换。

#### 转换为数字型
 ![[Pasted image 20220807124212.png]]
第一个输入小数会取整，包含单位会自动去掉%%也就是不会报错%%

注意 parseInt 和 parseFloat 单词的大小写

最后一个，只有+不可以隐式转换，不过可以-0减零来转换

案例：用户输入出生年份，算出年龄；简单加法器

#### 转换为布尔型
代表空、否定的值会被转换为 false ，如' '、0、 NaN、 null、 undefined
其余值都会被转换为 true  
![[Pasted image 20220807135719.png]]

所以数字里 只有0是false 其他都是true



## 运算符
- [[#运算符|运算符]]
	- [[#算数运算符|算数运算符]]
	- [[#递增和递减运算符|递增和递减运算符]]
	- [[#比较运算符|比较运算符]]
	- [[#逻辑运算符|逻辑运算符]]
	- [[#赋值运算符|赋值运算符]]

- [[#运算符优先级|运算符优先级]]

### 运算符
运算符 (operator）也被称为操作符，是用于实现赋值、比较和执行算数运算等功能的符号。
JavaScript 中常用的运算符有：
- [[#算数运算符|算数运算符]]
- [[#递增和递减运算符|递增和递减运算符]]
- [[#比较运算符|比较运算符]]
- [[#逻辑运算符|逻辑运算符]]
- [[#赋值运算符|赋值运算符]]


#### 算数运算符
概念：算术运算使用的符号，用于执行两个变量或值的算术运算。
![[Pasted image 20220809175742.png]]

浮点数进行运算会出现问题，这是计算机底层的问题

二进制的浮点数运算会有误差 (0.1 + 0.2) = 0.30000000000000004
0.3 用二进制无法准确表达，就像 1/3 用十进制也无法准确表达

浮点数值的最高精度是 17 位小数，但在进行算术计算时其精确度远远不如整数。

==避开浮点数==

##### 表达式和返回值
表达式：是由数字、运算符、变量等以能求得数值的有意义排列方法所得的组合
简单理解：是由数字、运算符、变量等组成的式子
表达式最终都会有一个结果，返回给我们，我们成为返回值 
eg：1+1
`=` 的意思是赋值（不是等于），所以应该倒着写 `var num = 1 + 1;` `2 = 1 + 1`
![[Pasted image 20220809182407.png]]

#### 递增和递减运算符
如果需要反复给数字变量添加或减去 1，可以使用 `递增(++）` 和 `递减（--）` 运算符来完成。

==注意==：递增和递减运算符必须==和变量配合==使用。

在JavaScript中，递增（++）和递减（--）既可以放在变量前面，也可以放在变量后面。放在变量前面时，我们可以称为**前置递增（递减）运算符**，放在变量后面时，我们可以称为**后置递增（递减）运算符**。

前置递增和后置递增运算符可以简化代码的编写，让变量的值＋1 比以前写法更简单
单独使用时，运行结果相同
与其他代码联用时，执行结果会不同
	后置：先原值运算，后自加（先人后己）
	前置：先自加，后运算（先已后人）
开发时，大多使用后置递增/減，并且代码独占一行，例如：num++;或者 num--;

1. 前置递增运算符
++num 前置递增，就是自加1，类似于 num = num +1，但是++num 写起来更简单。
使用口诀：先自加，后返回值

2. 后置递增运算符
num++ 后置递增，就是自加 1，类似于 num = num + 1，但是 num++ 写起来更简单。
使用口诀：先返回原值，后自加（也就是引号之后才产生效果）
 
var age = 10;
此时 age == age++ == ++ age == 11
age++ + 10 == 20
++age + 10 == 21



#### 比较运算符
概念：比较运算符（关系运算符）是两个数据进行比较时所使用的运算符，比较运算后，会返回一个布尔值 ( true / false）作为比较运算的结果。

![[Pasted image 20220809182146.png]]

`==` 默认转换数据类型，会把 string 转换为 number再进行比较


#### 逻辑运算符
概念：逻辑运算符是用来进行布尔值运算的运算符，其返回值也是布尔值。后面开发中经常用于多个条件的判断
![[Pasted image 20220809182528.png]]

[[逻辑门]]

##### 短路运算（逻辑中断）
短路运算的原理：当有多个表达式 (值）时左边的表达式值可以确定结果时，就不再继续运算右边的表达式的值
	&& 从左往右找假，找到返回，后面就不执行了，没有假就全部执行返回最后一个真
	|| 从左往右找真，找到返回，后面就不执行了，没有真就全部执行返回最后一个假

什么是真什么是假：[[#转换为布尔型]]

逻辑中断很重要 它==会影响我们程序运行结果==


#### 赋值运算符
概念：用来把数据赋值给变量的运算符。
![[Pasted image 20220809184313.png]]


### 运算符优先级
![[Pasted image 20220809184453.png]]

一元运算符里面的逻辑非优先级很高
逻辑与比逻辑或优先级高

判断的时候，先用[[#逻辑运算符]]隔开
![[Pasted image 20220809184656.png]]

事实上真正写代码的时候都会用小括号，提高可读性（因为自己也可能记不住）

## 流程控制
- [[#分支|分支]]
	- [[#分支#if 语句|if 语句]]
	- [[#分支#三元表达式|三元表达式]]
	- [[#分支#分支流程控制 switch 语句|分支流程控制 switch 语句]]
		- [[#分支流程控制 switch 语句#switch 语句和 if else if语句的区别|switch 语句和 if else if语句的区别]]
- [[#循环|循环]]
	- [[#循环#for 循环|for 循环]]
	- [[#循环#断点调试|断点调试]]
	- [[#循环#双重 for 循环|双重 for 循环]]
	- [[#循环#while 循环|while 循环]]
	- [[#循环#do while 循环|do while 循环]]
	- [[#循环#continue break|continue break]]
		- [[#continue break#continue|continue]]
		- [[#continue break#break|break]]
	- [[#循环#作业|作业]]


在一个程序执行的过程中，各条代码的执行顺序对程序的结果是有直接影响的。很多时候我们要通过控制代码的执行顺序来实现我们要完成的功能。
简单理解：==流程控制就是来控制我们的代码按照什么结构顺序来执行==

流程控制主要有三种结构，分别是**顺序结构、[[#分支|分支结构]]和[[#循环|循环结构]]**，这三种结构代表三种代码执行的顺序。
![[Pasted image 20220809185154.png]]
顺序结构是程序中最简单、最基本的流程控制，它没有特定的语法结构，程序会按照代码的先后顺序，依次执行，程序中大多数的代码都是这样执行的。


### 分支
由上到下执行代码的过程中，根据不同的条件，执行不同的路径代码（执行代码多选一的过程），从而得到不同的结果

JS 语言提供了两种分支结构语句
	if语句
	switch语句

#### if 语句
- if分支
- if else 双分支
- if else if 多分支

语法结构
```js
if (条件表达式){
执行语句1
} else {
执行语句2
}
```

执行思路：条件表达式为==真==(包括布尔值），则执行括号里的执行语句，否则 执行if语句后面的代码/else语句
![[Pasted image 20220809190020.png|200]] ![|200](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220812131352.png)

if 里面的语句 1 和 else 里面的语句 2 最终只能有一个语句执行 2 选 1
else后直接大括号，没有小括号（也就 是不用再限定条件）

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220812131545.png)


多分支语句 就是利用多个条件来选择不同的语句执行 得到不同的结果 多选1的过程
if else if语句是多分支语句

```js
if (条件表达式1){
执行语句1
} else if (条件表达式2) {
执行语句2
} else if (条件表达式3) {
执行语句3
} else if (条件表达式4){
执行语句4
} else {
最后的语句
}
```

- 执行思路
如果条件表达式1 满足就执行 语句1 执行完毕后，退出整个if 分支语句
如果条件表达式1不满足，则判断条件表达式2 满足的话，执行语句2 以此类推
如果上面的所有条件表达式都不成立，则执行else 里面的语句

- 注意点
多分支语句还是多选1 最后只能有一个语句执行
else if 里面的条件理论上是可以任意多个的
else if 中间有个空格
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220812132934.png)


#### 三元表达式

三元表达式也能做一些简单的条件选择。

有三元运算符组成的式子称为三元表达式
	一元表达式：++num
	二元表达式：3+5（算数表达式）
	二元表达式：？：

- 语法结构
条件表达式 `？` 表达式 1：表达式 2

- 执行思路
如果条件表达式结果为真 则 返回 表达式 1 的值 如果条件表达式结果为假 则返回 表达式 2 的值%%类似于简化版的 if else%%

- 代码体验
``` js
var num = 10；
var result = num ＞ 5 ? '是的' : '不是的' ；
```

- 案例分析 ：数字补 0
用户输入数字，如果数字小于 10，则在前面补 0 比如 01，09，如果数字大于 10，则不需要补，比如 20。

用户输入0~59之间的一个数字
如果效字小于10，则在这个数字前面补0（加0）否则 不做操作
用一个变量接受这个返回值，输出

[[#日期格式化]]

#### 分支流程控制 switch 语句

switch 语句也是多分支语句，它用于基于不同的条件来执行不同的代码。当要针对变量设置一系列的**特定值**%%不适合范围%%的选项时，就可以使用 switch。

- 语法结构
```js
switch(表达式){
	case value1:
		执行语句1;
		break;
	case value2:
			执行语句2;
		break;
	...
	default:
		执行最后语句;
}
```

注意：case和value之间要有空格；value之后是冒号；一定要写break

执行思路：匹配
利用 表达式的值 和 case 后面的选项值相匹配 如果匹配上，就执行该 case 里面的语句 如果都没有匹配上，那么执行 default 里面的语句

num 的值 和 case 里面的值相匹配的时候是 全等 必须是值和数据类型一致才可以

表达式一般是变量

- 案例：查询水果


##### switch 语句和 if else if语句的区别
- 一般情况下，它们两个语句可以相互替换
- Switch.case 语句通常处理case为比校确定值的情况，而if.else.语句更加灵活，常用于范国判断大于、等于某个范围）
- switch 语句进行条件判断后直接执行到程序的条件语句，效率更高。而 if. else 语句有几种条件，就得判断多少次。（匹配是直接跳到 case 执行，而 if 是顺序执行下来）
- 当分支比较少时，if...else语句的执行效率比 switch语句高。
- 当分支比较多时，switch 语句的执行效率比较高，而且结构更清晰。


### 循环
- 学习目的
	能够说出循环的目的
	能够说出 for 循环的执行过程
	能够使用断点调试来观察代码的执行过程
	能够使用 for循环完成累加求和等案例
	能够使用双重 for 循环完成乘法表案例
	能够说出 while 循环和 do while 循环的区别
	能够说出 break 和 continue 的区别

循环的目的：可以**重复执行**某些代码
	实际问题中，有许多具有规律性的重复操作，因此在程序中要完成这类操作就需要重复执行某些语句

在[[JavaScript]]中，主要有三种类型的循环语句：
	for 循环 🌟
	while 循环
	do...while 循环

三个循环很多情况下都可以相互替代使用
如果是用来**计次数**，跟数字相关的，三者使用基本相同，但是我们更喜欢用 for
while 和 do.. while 可以做**更复杂的判断条件**，比 for 循环灵活一些
while 和 do.. while 执行顺序不一样，while 先判断后执行，do.. while 先执行一次，再判断执行
while 和 do..while 执行次数不一样，do.while 至少会执行一次循环体，而 while 可能一次也不执行
实际工作中，我们更常用 **for 循环**语句，它写法更简洁直观，所以这个要重点学习




#### for 循环
在程序中，一组被重复执行的语句被称之为**循环体**，能否继续重复执行，取决于循环的**终止条件**。由循环体及循环的终止条件组成的语句，被称之为**循环语句**

语法结构
for 循环主要用于把某些代码循环若干次，通常跟==计数==有关系。其语法结构如下：
``` js
for (初始化变量;条件表达式;操作表达式){
循环体
}
```

- 三个选项一个都不能少
	初始化变量：就是用 var 声明的一个普通变量，通常用于作为**计数器**使用
	条件表达式：就是**终止条件**，决定每一次循环是否继续执行
	操作表达式：每次循环最后执行的代码，经常用于计数器变量进行**更新**（递增或递减）

顺序：先执行循环体，再更新操作表达式
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220815012220.png)

---
我们可以让用户控制输出的次数
```js
var num prompt(“请您输入次数”）;
for (var i=1；i<= num；i++){
}
```

---

for 循环重复**不相同的代码**
for 循环还可以重复不同的代码，这主要是因为使用了计数器，计数器在每次循环过程中都会有变化。

- 案例：我们想要输出1个人 1~100岁
```js
for (var i = 1; i <= 100; i++) {
	if (i == 1) {
		console.log("这个人出生了");
	} else if (i == 100) {
		console.log("这个人死了");
	} else {
		console.log("这个人今年" + i + "岁了")
	}
}
```

---
for 循环重复某些**相同操作**
for 循环因为有了计数器的存在，我们还可以重复的执行某些操作，比如做一些算术运算。

- 案例 1：求 1-100 之间所有整数的累加和

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220815145523.png)

```js
	let sum = 0
	for (var i = 1; i <= 100; i++) {
		sum += i
	}
	alert(sum)
```

结果是5050

- 1-100 奇书和 偶数和

```js
	let even = 0, odd = 0
	for (var i = 1; i <= 100; i++) {
		if (i % 2 == 0) {
			even += i
		} else {
			odd += i
		}
	}

	alert("奇书和" + odd + "偶数和" + even)
```


#### 断点调试

断点调试是指自己在程序的某一行设置一个断点，调试时，程序运行到这一行就会停住，然后你可以一步一步往下调试，调试过程中可以看各个变量当前的值，出错的话，调试到出错的代码行開显示错误，停下。

**断点调试可以帮我们观察程序的运行过程**

[[浏览器开发者工具]]--> sources--＞找到需要调试的文件-->在程序的某一行设置断点（再刷新一下才会成功设置）
Watch:监视，通过watch可以监视变量的值的变化，非常的常用。
F11: 程序单步执行，让程序一行一行的执行，这个时候，观察 watch 中变量的值的变化。

代码调试的能力非常重要，只有学会了代码调试，才能学会自己解决 bug 的能力。初学者不要觉得调试代码麻烦就不去调试，知识点花点功夫肯定学的会，但是代码调试这个东西，自己不去练，永远都学不会。

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220815145523.png)

一行打印五颗星星 🌟🌟🌟🌟🌟
采取追加字符串的方式，空字符串重复叠加5次🌟，输出1次（而不是一次直接输出一颗🌟，输出5次）
 
#### 双重 for 循环

循环嵌套

很多情况下，单层 for 循环并不能满足我们的需求，比如我们要打印一个 5 行 5 列的图形、打印一个倒直角三角形等，此时就可以通过循环嵌套来实现。

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220815162658.png)

循环嵌套是指<font color=#F36208>在一个循环语句中再定义一个循环语句的语法结构</font>，例如在for循环语句中，可以再嵌套一个for 循环，这样的 for 循环语句我们称之为**双重for循环**。

语法结构
``` js
for (外层初始化变量;外层条件表达式;外层操作表达式){
	for (里层初始化变量;里层条件表达式;里层操作表达式){
	执行语句
	}
}
```

把里面的循环看做是外层循环的语句，外层循坏循环一次，里面的循环执行全部

外层控制行数，内层控制列数 

- 案例 打印固定行列数🌟
```js
	var print = ""
	var rows = prompt("请问你想打印几行？")
	var cols = prompt("请问你想打印几列？")
	for (i = 1; i <= rows; i++) {
		for (j = 1; j <= cols; j++) {
			var print = print + "🌟"
		}
		var print = print + "\n"
	}
	console.log(print)
```

- 倒三角星星 （j = i 倒三角）
```js
	var print = ""
	for (i = 1; i <= 10; i++) {
		for (j = i; j <= 10; j++) {
			var print = print + "🌟"
		}
		var print = print + "\n"
	}
	console.log(print)

```





- 九九乘法表（ j<=i 正三角）
```js
	var str = "";
	for (i = 1; i <= 9; i++) {
		for (j = 1; j <= i; j++) {
			str += j + "x" + i + "=" + i * j + " "
		}
		var str = str + "\n"
	}
	console.log(str)
```

- 小结
	- for 循环可以重复执行某些相同代码
	- for 循环可以重复执行些许不同的代码，因为我们有计数器
	- for 循环可以重复执行某些操作，比如算术运算符加法操作
	- 随着需求增加，双重for循环可以做更多、更好看的效果
	- 双重 for 循环，外层循环一次，内层 for 循环全部执行
	- for 循环是循环条件和数字直接相关的循环
	- 分析要比写代码更重要（知难行易）



#### while 循环
while 语句可以在条件表达式为真的前提下，循环执行指定的一段代码，直到表达式不为真时结束循环。可以做一些==更复杂的条件判断==（[[#if 语句]]是计数）

while = 当...的时候

语法结构
``` js
while (条件表达式) {
循环体代码
}
```

```js
var num = 1; //计数器
while(num<=100){
console.log("xxx")
num++; //操作表达式
}
```

里面应该也有计数器 初始化变量
里面应该也有操作表达式(不要忘记！否则会死循环) 完成计数器的更新 防止死循环


执行思路：
- 先执行**条件表达式**，如果结果为 true，则执行循环体代码；如果为 false，则退出循环，执行后面代码
- 执行**循环体**代码
- 循环体代码执行完毕后，程序会**继续判断执行条件表达式**，如条件仍为true，则会继续执行循环体，直到循环条件为 false 时，整个循环过程才会结束

- 案例：你爱我吗？

```js
var message = prompt("你爱我吗"); //多写了一次
while (message !== "我爱你") {
	var message = prompt("你爱我吗");
} 
alert ("我也爱你")
```

#### do while 循环
do.. while 语句其实是 while 语句的一个**变体**。
该循环会**先执行**一次代码块，然后**再**对条件表达式进行**判断**，如果条件为真，就会重复执行循环体，否则退出循环。（先斩后奏，至少可以执行一次）

语法结构
```js
do{
循环体;
i++;
} while()
```

- 案例

```js
do {
	var message = prompt("你爱我吗"); //直接问
} while (message !== "我爱你")
alert ("我也爱你")
```


#### continue break
##### continue
continue 关键字用于立即跳出本次循环，继续下一次循环（本次循环体中 continue 之后的代码就会少执行一次）。

例如，吃 5 个包子，第 3 个有虫子，就扔掉第 3 个，继续吃第 4 个第 5 个包子，其代码实现如下：
```js
for (var i = 1; i <= 5; i++) {
	if (i == 3) {
		continue;
	}
	console.log("我正在吃第" + i + "个包子")
}
```


场景（除了）：求1~108 之间，除了能被7整除之外的整数和

##### break
break 关键字用于立即**跳出整个循环**（循环结束）。
例如，吃5个包子，吃到第3个发现里面有半个虫子，其余的不吃了，其代码实现如下：


#### 作业
求1-100之间所有数的总和与平均值
求1-100之间所有偶数的和
求100以内7的倍数的总和
使用 for 循环打印矩形，要求每次只能输出一个🌟
使用 for 循环打印三角形
使用for循环打印99乘法表
接收用户输入的用产名和密码，若用户名为 、admin”，密码为 〝123456" ，则提示用户登录成功！否则，让用户一直输入。
求整数1～100的累加值，但要求跳过所有个位为3的数【用continue实现】。

简易 ATM
里面现存有 100块钱。
如果存钱，就用输入钱数加上先存的钱数，之后弹出显示余额提示框
如果取钱，就减去取的钱数，之后弹出显示余额提示框
如果显示余额，就输出余额
如果退出，弹出退出信息提示框

## 数组
[[#数组对象]]

能够知道为什么要有数组
能够创建数组
能够获取数组中的元素
能够对数组进行遍历
能够给数组新增一个元素
能够独立完成冒泡排序的案例

### 数组的概念
问：之前学习的变量，只能存储一个值。如果我们想存储班级中所有学生的姓名，那么该如何存储呢？
答：可以使用数组 (Array)。<font color=#F36208>数组可以把一组相关的数据一起存放，并提供方便的访问（获取）方式</font>。

什么是数组？：数组是指**一组数据的集合**，其中的每个数据被称作**元素**，在数组中可以**存放任意类型的元素**。数组是一种**将一组数据存储在单个变量名下**的优雅方式。
%%和python列表差不多🤔%%

### 创建数组
JS中创建数组有两种方式：
	利用 new 创建数组
	利用数组[[#^31bb98|字面量]]创建数组：`[ ]` 🌟

```js
var arr = new Array(2); //2的意思不是里面有元素2，而是数组长度为2，里面有2个空元素
var arr = new Array(2,3); //意思是有两个元素2,3
```

```js
var 数组名 = [1,2,"我",true];
```

数组里面的数据一定用逗号分隔

数组里面的数据 比如 1，2，我们称为数组元素

数组中可以存放任意类型的数据，例如字符串，数字，布尔值等。

声明数组并赋值称为**数组的初始化**


### 获取数组中的元素(索引)

索引(下标)：用来访问数组元素的序号（数组下标==从0开始==）。
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220816123804.png)


数组可以通过索引来**访问**、设置、修改对应的数组元素，我们可以通过 `数组名[索引号]` 的形式来获取数组中的元素。

这里的访问就是获取得到的意思
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220816124109.png)

```js
console.log(arr[2]);
```

### 遍历数组
- 怎么把数组里面的元素全部取出来？
	规律：从代码中我们可以发现，从数组中取出每一个元素时，代码是重复的，有所不一样的是索引值在递增
	答案就是 [[#循环]]

遍历：就是把数组中的每个元素从头到尾都访问一次（类似我们每天早上学生的点名）。
```js
        var week = ["星期一", "星期二", "星期三", "星期四", "星期五", "星期六", "星期天"];
        for (var i = 0; i < 7; i++) {
            console.log(week[i]);
        }
```

我们的数组索引号从 0 开始，所以 i 必须从 0 开始
也可以写成 i>=6，但是 7 更符合认知更好判断

### 数组长度
![[JavaScript#^jr4ek3]]
使用“`数组名.length`”可以访问数组元素的数量（数组长度）。

- 数组的长度是元素个数 不要跟[[#获取数组中的元素 索引|索引号]]混淆
	- 数组索引号和数组长度有什么关系？ 索引号从0开始，数组长度是元素个数

- arr. length 动态监测数组元素的个数
```js
        for (var i = 0; i < arr.length; i++) {
            console.log(arr[i]);
        }
```


- 案例：求数组[2,6,1,7,4] 里面所有元素的和以及平均值。
```js
	var arr = [2, 6, 1, 7, 4]
	var sum = 0
	for (i = 0; i < arr.length; i++) {
		sum += arr[i]
		average = sum / arr.length
	}
	console.log(sum, average);
```
想要输出多个变量，用逗号分隔即可

- 数组转换为分割字符串
```js
	var arr = ['red', 'green', 'blue', 'pink']
	var str = ''
	for (i = 0; i < arr.length; i++) {
		str = arr[i] + "|" + str
	}
	console.log(str);
```

- 求数组中的最大值
思路：打擂台

```js
	var arr = [2, 6, 1, 77, 52, 25, 7]
	var max = arr[0] //max 不要写 0 因为数组里的数可能是负数
	for (i = 0; i < arr.length; i++) {
		if (arr[i] > max) {
			max = arr[i]
		}
	}
	console.log(max);
```


### 数组中新增元素
可以通过 1. 修改 length 长度 以及 2. 索引号 增加数组元素

#### 通过修改 length 长度新增数组元素

可以通过修改 length 长度来实现数组扩容的目的

length 属性是可读写的
```js
	var arr = ['red', 'green', 'blue', 'pink'];
	arr.length = 5;
	console.log(arr);
```

结果是(5)`['red', 'green', 'blue', 'pink', empty]`

其中索引号是4的空间没有给值，就是声明变量未给值，默认值就是 undefined.


#### 通过修改数组索引新增数组元素

可以通过修改数组索引的方式**追加**数组元素

```js
	var arr = ['red', 'green', 'blue'];
	arr[3] = 'pink';
	console.log(arr);
```

结果是`['red', 'green', 'blue', 'pink']`

追加已有的会**替换**原来的数组元素
`arr[0] = 'pink';`

不要直接给 数组名赋值 否则里面的数组元素都会被覆盖消失

- 数组新增元素
新建一个数组，里面存放10个整数（1~10）

```js
	var str = []
	for (i = 0; i < 100; i++) {
		str[i] = i + 1
	}
	console.log(str);
```


- 筛选数组
要求：将数组 [2,0,6,1,77,0,52,0,25,7]中大于等于10的元素选出来，放入新数组。
```js
	var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
	var newArr = [];
	var j = 0; //解决新数组的序号问题
	for (i = 0; i < arr.length; i++) {
		if (arr[i] >= 10) {
			newArr[j] = arr[i];
			j++;
		}
	}
	console.log(newArr);
```

```js
	var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
	var newArr = [];
	for (i = 0; i < arr.length; i++) {
		if (arr[i] >= 10) {
			newArr[newArr.length] = arr[i]; //newArr.length 长度就是最后一个 自动更新
		}
	}
	console.log(newArr);
```


### 数组案例

#### 课堂案例1：删除指定数组元素
要求：特数组[2,0,6,1,77,0,52,0,25,7]中的0去掉后，形成一个不包含0的新数组。

```js
	var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7]
	var newArr = []
	for (i = 0; i < arr.length; i++) {
		if (arr[i] > 0) {
			newArr[newArr.length] = arr[i]
		}
	}
	console.log(newArr);
```


#### 课堂案例2：翻转数组
要求：将数组 ['red','green','blue','pink','purple']的內容反过来存放。
输出：['purple','pink', 'blue','green', 'red']
```js
	var arr = ['red', 'green', 'blue', 'pink', 'purple'];
	var newArr = [];
	for (i = 0; i < arr.length; i++) {
		newArr[arr.length - 1 - i] = arr[i];
	}
	console.log(newArr);
```

#### 课堂案例 3：数组排序（冒泡排序）

sort 排序

我们先复习下如何把 2 个变量交换数据 [[#交换变量案例|交换变量案例]]

冒泡排序：是一种算法，把一系列的数据**按照一定的顺序**进行排列显示(从小到大或从大到小）。

摘要
冒泡排序是一种简单的排序算法。它重复地走访过要排序的数列，**一次比较两个元素**，如果他们的顺序错误就把他们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。
这个算法的**名字由来**是因为越小的元素会经由交换慢慢“浮”到数列的顶端。

什么是算法？
观察执行过程，找到其中规律，从而转换成代码 ^qz7zjv

1. 一共需要的趟数 我们用外层for 循环
	5个数据我们一共需要走4趟
	长度就是数组长度 减去 1 `arr.length -1`
2.每一趟交换次数 我们 用里层 for循环
	第一趟交换4次
	第二趟交换3次
	第三超交换2次
	第四趟交換1次
	长度就是数组长度 减去 次数
	但是我们次数是从0次开始的 所以 最终 `arr.length-i-1`
3. 交换2个变量就好了

趟数：从头到尾走一遍叫做一趟

```js
        var arr = [5, 4, 3, 2, 1]
        for (i = 0; i < arr.length - 1; i++) { //外层循环管趟数
            for (j = 0; j <= arr.length - i - 1; j++) { //里面的循环管 每一趟的交换次数
                //内部交换2个变量的值
                if (arr[j] > arr[j + 1]) {
                    var temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp
                }
			}
        }
        console.log(arr);
```

## 函数

能够说出为什么需要函数
能够根据语法书写函数
能够根据需求封装函数
能够说出形参和实参的传递过程
能够使用函数的返回值
能够使用arguments获取函数的参数


- [[#函数的概念|函数的概念]]
- [[#函数的使用|函数的使用]]
	- [[#函数的使用#声明函数|声明函数]]
	- [[#函数的使用#调用函数|调用函数]]
- [[#函数的参数|函数的参数]]
- [[#函数的返回值|函数的返回值]]
- [[#通过榨汁机看透函数|通过榨汁机看透函数]]
- [[#arguments 的使用|arguments 的使用]]
- [[#函数案例|函数案例]]
- [[#函数的两种声明方式|函数的两种声明方式]]


### 函数的概念

函数：就是==[[ALOA|封装]]了一段可被重复调用执行的代码块==。
	函数的封装是把一个或者多个功能通过函数的方式封装起来，对外只提供一个简单的函数接口
目的：通过此代码块可以实现大量代码的重复使用。

先定义 后调用

### 函数的使用

函数在使用时分为两步：声明函数和调用函数。

#### 声明函数

```js
function 函数名(){
函数体
}
```

```js
function sayHi()P
console.log('hi~')
```

- function 声明函数的关键字 全部小写
- 函数是做某件事情，函数名一般是动词
- 函数不调用，自己不执行（声明函数本身井不会执行代码，只有调用函数时才会执行函数体代码。）
	- 所以执行顺序是先读取调用，再回头找声明 

#### 调用函数
``` js
函数名();
```

``` js
sayHi();
```

调用函数的时候千万不要忘记加小括号


### 函数的参数
我们可以利用函数的参数实现函数重复不同的代码

- 形参和实参


 ![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220817140145.png) 



```js
function 函数名(形参1,形参2...){ ///在声明函数的小括号里面是 形参（形式上的参数）

}
函数名(实参,实参2...); //在函数调用的小括号里面是实参（实际的参数）
```

形参和实参的执行过程

```js
	function cook(aru) { //形参是接受实参的 aru = '酸辣土豆丝'  形参类似于一个变量
		console.log(aru);
	}

	cook("酸辣土豆丝");

```

函数的参数可以有，也可以没有，个数不限

多个参数之间用逗号隔开
形参可以看做是不用声明的变量


- 函数形参和实参个数不匹配问题

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220817143220.png)

js比较自由，形参实参可以不匹配，如果是java/c++ 会直接报错

建议：尽量让实参的个数和形参相匹配

### 函数的返回值

- return 返回函数
返回值（alert、console(log)）放在函数内部是很不合理的
	比喻：厨师自己做完菜自己吃了

我们函数只是实现某种功能，最终的结果需要返回给函数的调用者
	谁点的菜就给谁上菜

通过 `return`来实现

```js
        function 函数名(){
            return 需要返回的结果;
        }
        console.log(函数名());
```

只要函数遇到到return 就把后面的结果 返回给函数的调用者 函数名()=return后面的结果

```js
	// 利用函数求任意两个数的最大值-----
	function findBigger(num1, num2) {
		return num1 > num2 ? num1 : num2; //[[#三元表达式]]
	}
	console.log(findBigger(100, 9));
```


```js
	//利用函数求数组 [5,2,99,101,67,77]中的最大数值。----
	function getArrMax(arr) { //arr接受一个数组
		var max = arr[0]
		for (i = 0; i <= arr.length; i++) {
			if (arr[i] > max) {
				max = arr[i];
			}
            }
            return max;
        }
        var result = getArrMax([5, 2, 99, 101, 67, 77]) //实参是一个数组送过去,直接把结果复制给变量
        console.log(result); 
```

- return 终止函数

类似[[#break]]，函数内 return 后的代码不会被执行，return 应该出现在最后

-  return 的返回值
return 只能返回**一个值**。如果用逗号隔开多个值，以**最后一个**为准。
想要返回多个的话可以用[[#数组]] `return []`

我们的函数如果有 return，则返回的是 return 后面的值；
如果函数没有 return，则返回undefined

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220817153004.png)

[[#continue break]]

### 通过榨汁机看透函数
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220817153145.png)


### arguments 的使用
%%实参由用户输入，所以不能确定，当不确定参数数的时候用arguments%%
当我们不确定有多少个参数传递的时候，可以用 **arguments** 来获取。
在 JavaScript 中，arguments 实际上它是当前函数的一个**内置对象**。所有函数都内置了一个 arguments 对象，arguments 对象中存储了传递的所有实参。

```js
	function fn() {
		console.log(arguments); //里面存储了所有传递过来的实参
	}
	fn(1, 2, 3);
```

arguments 展示形式是一个**伪数组**，因此可以进行遍历。

伪数组并不是真正意义上的数组，它具有以下特点：
	具有 length 属性
	按索引方式储存数据（我们可以按照数组的方式遍历arguments）
	不具有数组的 push, pop 等方法

只有函数才有 arguments对象 而且是每个函数都内置好了这个arguments（不需要额外声明）

```js
////利用函数求任意个数的最大值
        function getMax() {
            var max = arguments[0];
            for (i = 0; i <= arguments.length; i++) {
                if (arguments[i] > max) {
                    max = arguments[i];
                }
            }
            return max;
        }
        console.log(getMax(5, 2, 99, 101, 67, 77));
```


### 案例

- 闰年

- 用户输入年份，输出当前年份2月份的天数

- 函数可以调用另一个函数
因为每个函数都是独立的代码块，用于完成特殊任务，因此经常会用到函数相互调用的情况。
记住函数的顺序是先调用再回头声明



### 函数的两种声明方式

- 利用函数关键字自定义函数（命名函数）

```js
function fn(){

}
fn();
```

- 函数表达式（匿名函数） ^p6aes2

```js
var 变量名 = function(){};
var fun = function(){}
```

这个函数没有名字，fun是变量名，所以是匿名的

函数表达式声明方式跟[[#声明变量]]差不多，只不过变量里面存的是值，而函数表达式里面存的是函数

函数表达式也可以进行传递参数

## JavaScript 作用域
能够说出 JavaScript的两种作用域
能够区分全局变量和局部变量
能够说出如何在作用域链中查找变量的值

### 作用域
通常来说，一段程序代码中所用到的名字并不总是有效和可用的，而==限定这个名字的可用性的代码范围==就是这个名字的作用域。作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字沖突。

Javascript 作用域：就是代码名字 ==在某个范围内起作用和效果== 目的是为了提高程序可靠性、减少命名冲突

js 的作用域 (es6%%es=ecma 的缩写，标准协会的名字%%之前)：全局作用域、局部作用域

全局作用域：整个 script 标签 / 一个单独的 js 文件
	所有函数的最外层被称为全局作用域。 在全局作用域内定义的值可以在任意地方访问。

局部作用域（函数作用域）：在函数内部就是局部作用域。这个代码的名字只在函数内部起效果和作用

```js
var num = 10 //全局作用域
function fn(){
//局部作用域
var num = 20
}
//两者不冲突
```

#### 作用域与冲突
我们来谈一谈 [scope](https://developer.mozilla.org/zh-CN/docs/Glossary/Scope)即作用域 — 处理函数时一个非常重要的概念。当你创建一个函数时，函数内定义的变量和其他东西都在它们自己的单独的范围内，意味着它们被锁在自己独立的隔间中，不能被函数外的代码访问。

由于安全性和组织性。有时您不希望变量可以在代码中的任何地方访问 - 您从其他地方调用的外部脚本可能会开始搞乱您的代码并导致问题，因为它们恰好与代码的其他部分使用了相同的变量名称，造成冲突。

这有点像一个动物园。狮子，斑马，老虎和企鹅都保留在自己的园子中，只能拿到到它们园子中的东西 —— 与其函数作用域相同。如果他们能进入其他园子，就会出现问题。不同的动物会在不熟悉的栖息地内感到真的不舒服 - 一只狮子或老虎会在企鹅的水多的，冰冷的的领域中感到可怕。最糟糕的是，狮子和老虎可能会尝试吃企鹅！

### 变量的作用域

在JavaScript中，根据作用域的不同，变量可以分为两种：全局变量、局部变量

- 全局变量：1. 在全局作用域下的变量，在全局下都可以使用
注意： 2. 如果在函数内部 没有声明直接赋值的变量也属于全局变量（不建议使用）

```js
var num = 10 //num就是一个全局变量
function fn(){
var num = 20 //num1就是局部变量 只能在函数内部使用
}
```


- 局部变量：在局部作用域下的变量；在函数内部的变量就是 局部变量
注意：函数的[[#形参]]也可以==看做是==局部变量

- 从执行效率来看全局变量和局部变量
	全局变量只有浏览器关闭的时候才会销毁，比较占内存资源
	局部变量 当我们程序执行完毕就会销毁，比较节约内存资源

- 现阶段我们 js 没有 块级作用域，我们 js 也是在 es6 的时候新增的块级作用域
	{} 花括号里包含的就是块级作用域


### 作用域链

只要是代码，就至少有一个作用域

写在函数内部的叫局部作用域

如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域

根据在**内部函数可以访问外部函数变量**的这种机制，用链式查找决定哪些数据能被内部函数访问，就称作**作用域链**

**就近原则**：站在目标出发，一层一层的往外查找

像这种情况嵌套函数，而且变量名字全局跟局部相同的情况下，优先访问外部函数的变量，而不是全局作用域的变量



![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220818224113.png)

## JavaScript 预解析
能够知道解析器运行JS分为哪两步
能够说出变量提升的步骤和运行过程
能够说出函数提升的步骤和运行过程

### 预解析画
%%not defined 报错 和  undefined值是不一样的 ，一个没有声明，一个声明了没赋值%%

JavaScript 代码是由浏览器中的 JavaScript 解析器来执行的。JavaScript 解析器在运行 JavaScript 代码的时候分为两步：预解析和代码执行。

- 预解析：js 引擎会把 js 里面所有的 var 还有 function 提升到当前作用域的最前面
- 代码执行：按照代码书写的顺序从上往下执行


### 变量预解析和函数预解析

预解析分为 变量预解析（变量提升）和 函数预解析（函数提升）

- 变量提升 就是把所有的**变量声明**提升到当前的作用域最前面 **不提升赋值**操作
	- var 是 声明，=是赋值
	- ![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220818225520.png)
	- 提升了个寂寞

- 函数提升 就是把所有的函数声明提升到当前作用域的最前面 不调用函数
	- ![[JavaScript#^p6aes2]]不能提升，只能提升声明的函数




### 预解析案例
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220818233931.png)


[[#声明变量]] 集体声明 和 全局变量的特殊情况

结果：99999 not defined 错误

## 对象
能够说出为什么需要对象
能够使用字面量创建对象
能够使用构造函数创建对象
能够说出 new 的执行过程
能够遍历对象

1. 对象可以让代码结构更清晰
2. 对象复杂数据类型object.
3. 本质：对象就是一组无序的相关属性和方法的集合。
4. 构造函数泛指某一大类，比如苹果，不管是红色苹果还是绿色苹果，都统称为苹果。
5. 对象实例特指一个事物，比如这个苹果、正在给你们讲课的pink老师等。
6. for..in 语句用于对对象的属性进行循环操作。

### 对象

现实生活中：万物皆对象，对象是**一个具体的事物**，看得见摸得着的实物。例如，一本书、一辆汽车、一个人可以是“对象〞，一个数据库、一张网页、一个与远程服务器的连接也可以是“对象”。

在 JavaScript 中，对象是一组**无序**的相关**属性**和**方法**的集合，所有的事物都是对象，例如字符串、数值、数组、函数等。

对象是由**属性和方法**组成的。
	属性：事物的特征，在对象中用属性来表示（常用名词）
	方法：事物的行为，在对象中用方法来表示（常用动词）

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220819000820.png)


保存一个值时，可以使用变量，保存多个值（一组值）时，可以使用数组。如果要保存一个人的完整信息呢？

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220819001031.png)




### 创建对象的三种方式
在 JavaScript中，现阶段我们可以采用三种方式创建对象(object)

#### 利用字面量创建对象
对象字面量：就是花括号 `{} ` 里面包含了表达这个具体事物（对象）的属性和方法。

`()` ：运算符（优先级最高）
`[]` ：数组
`{}` ：对象

```js
	var obj = {
		unma: "关念", //属性 
		age: 12,
		sex: male,
		sayHi: function () {  //方法
			console.log("hi")
		}
	}
```

- 里面的属性或者方法我们采取键值对的形式
	- 键 属性名：值 属性值
		键：相当于属性名
		值：相当于属性值，可以是任意类型的值（数字类型、字符串类型、布尔类型，函数类型等）
	多个属性或者方法中间用逗号隔开的
	方法冒号后面跟的是一个匿名函数

##### 变量、函数、属性、方法的区别

变量和属性的相同点 他们都是用来存储数据的
	变量 单独声明并赋值 使用的时候直接写变量名
	属性 在对象里面的不需要声明的 使用的时候必须是 对象.属性

函数和方法的相同点 都是实现某种功能 做某件事
	函数是单独声明 并且调用的 函数名() 单独存在的
	方法 在对象里面 调用的时候 对象. 方法 ()


#### 利用 new Object 创建对象

跟我们前面学的[[#创建数组]] new ArrayO 原理一致

```js
	var obj = new Object();
	obj.name = "关念";
	obj.age = 15;
	obj.sex = "female"
	obj.sayHi = function (){
	console.log("hi")
	}
```

1. 我们是利用 **等号赋值**的方法 添加对象的属性和方法
2. 每个属性和方法之间用 **分号**结束 %%书写规范不太一样，原理是一样的%%

#### 利用构造函数创建对象

- 我们为什么需要使用构造函数？

我们前面两种创建对象的方式一次只能创建一个对象，然而里面很多的属性和方法是大量相同的 我们只能复制

因此我们可以利用函数的方法 重复这些相同的代码 我们就把这个函数称为 **构造函数**
	因为这个函数不一样，里面封装的不是普通代码，而是 对象

构造函数 就是把我们对象里面一些相同的属性和方法抽象出来封装到函数里面
	抽象 封装 抽风hhh


- 构造函数的语法格式

```js
	function 构造函数名() {
		this.属性 = 值;
		this.方法 = function () {

		}
	}
	new 构造函数名();

```

注意：1. 要写 `this.` 2. 用`new`调用 3.构造函数名首字母要大写 4.构造函数不需要return就可以返回结果

```js
	function Star(uname, age, sex) {
		this.name = uname
		this.age = age;
		this.sex = sex;
		this.sing = function(song){
			console.log(song)
		}	
	}
	var ldh = new Star("刘德华", 18, "男"); //调用函数返回的是一个对象
	console.log(ldh.name)
	ldh.sing("冰雨")
	var zxy = new Star("张学友",19,"男");
```

好处：可以批量生产

我们只要new star() 调用函数就创建一个对象 ldh {}


- 作业
```js
	function Character(name, type, blood, attack) {
		this.name = name;
		this.type = type;
		this.blood = blood;
		this.attack = attack;
	}
	var lp = new Character("廉颇", "力量型", 500, "近战")
	var hy = new Character("后羿", "射手型", 100, "远程")
	console.log(lp.name, hy.blood);
```

##### 构造函数和对象区别
- 对象 是一个具体的事物 eg 刘德华
- 构造函数  泛指的某一大类 eg 明星
	类似于java里面的「类」

- 我们利用构造函数创建对象的过程我们也称为**对象的实例化**

##### new 关键字
1. new 构造函数可以在内存中创建了一个空的对象
2. this 就会指向刚才创建的空对象
3. 执行构造函数里面的代码，给这个空对象添加属性和方法
4. 返回这个对象%%构造函数不需要return的原因%%

比喻：1.开了一个新坑 2.这个坑是我自己喜欢的 3.填坑ing 4.获得回报

### 调用对象

调用对象的**属性** 我们采取 `对象名.属性名` `.`立即为“的”
`console.log(obj.name);`

还有一种方法 `对象名["属性名"]` ==必须加引号==
`console.log(obj['age']);`

调用对象的**方法** `对象名.方法名()` ==千万别忘了小括号==

### 判断对象里是否有某个属性
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821001735.png)



### 遍历对象属性

不能用for遍历，因为对象里面的元素没有序号

for...in 语句用于对数组或者对象的属性进行循环操作。（最适合对象）

语法结构
```js
for (变量 in 对象){

}
```

```js
for (var k in obj) {
	console.log(k); //k 变量 输出 得到的是 属性名
	console.log(obj[k]); // obj[k] 得到是 属性值
}
```

- 为什么是k？
那是一个变量就是可以随便变，也就是说你就算写一个拼音 abcdefg 什么的都可以，数字字符串之类的好像不行
只是使用 for in 里面的变量 我们喜欢/习惯写 k 或者 key （约定俗成 没有规定 类似`i` `j`）

注意：k是变量，不加引号

## 内置对象
能够说出什么是内置对象
能够根据文档查询指定APl的使用方法
能够使用 Math 对象的常用方法
能够使用 Date 对象的常用方法
能够使用 Array 对象的常用方法
能够使用 String 对象的常用方法


### 内置对象
JavaScript中的**对象分为3种**：自定义对象、内置对象、浏览器对象

前面两种对象是JS基础内容，属于 ECMAScript；第三个浏览器对象属于我们JS独有的，我们JSAPI讲解

内置对象 就是指 JS 语言自带的一些对象，这些对象供开发者使用，并提供了一些封装好了的 常用的或是最基本而必要的功能（属性和方法）[[ALOA]]

内置对象最大的优点就是帮助我们快速开发

JavaScript 提供了多个内置对象：Math、 Date、 Array、 String 等

>[JavaScript 标准内置对象 - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects)
> 
> JavaScript 有许多内置的函数，可以让您做很多有用的事情，而无需自己编写所有的代码。事实上，许多你调用（运行或者执行的专业词语）浏览器内置函数时调用的代码并不是使用 JavaScript 来编写——大多数调用浏览器后台的函数的代码，是使用像 C++这样更底层的系统语言编写的，而不是像 JavaScript 这样的 web 编程语言。
> 
> 请记住，这些内置浏览器函数不是核心 JavaScript 语言的一部分——被定义为浏览器[[API]]的一部分，它建立在默认语言之上，以提供更多的功能。


### 查文档

学习一个内置对象的使用，只要学会其常用成员的使用即可，我们可以通过查文档学习，可以通过 MDN/3C 来查询。

[MDN Web Docs](https://developer.mozilla.org/en-US/)

Mozilla 开发者网络（MDN ) 提供了有关开放网络技术（Open Web）的信息，包括 HTML、 CSS 和万维网及 HTML5 应用的 APl.

#### 如何学习对象中的方法
1. 查阅该方法的功能
2. 查看里面参数的意义和类型
3. 查看返回值的意义和类型
4. 通过 demo 进行测试

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220819152459.png)
中括号`[]` 的意思：可以有可以没有




### Math 对象

[Math - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math)

`Math` 不是一个构造器：math不是[[#利用构造函数创建对象|构造函数]]，所以我们不需要new 来调用 而是直接使用里面的属性和方法即可

Math 它具有数学常数和函数的属性和方法。跟数学相关的运算（求绝对值，取整、最大值等）可以使用 Math 中的成员。
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220819153918.png)

四舍五入 5 往大了取（负数的情况）

#### 随机数方法 random ()
[Math.random() - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)

random () 返回一个随机的小数（浮点数）范围 `[0,1)`

这个方法里面不跟参数

##### 得到一个两数之间的随机整数 并且 包含这 2 个整数
`Math.floor(Math.random()*(max-min+1))+min;`

- 封装进函数
```js
function getRandom(min,max){
	return Math.floor(Math.random()*(max-min+1))+min;
}
```

- 随机点名
```js
var arr = ['张三'，'张三丰'，'张三疯子'，'李四'，'李思思'];
console.log(arr[gerRandom(0,arr.length - 1)]); //索引号是随机数
```

- 猜数字游戏
```js
//我写的
	function getRandom(min, max) {
		return Math.floor(Math.random() * (max - min + 1)) + min;
	}
	var number = getRandom(1, 10);
	var guessNumber = prompt("你猜是什么数字？");


	do {
		if (guessNumber < number) {
			alert("猜小了！");
			var guessNumber = prompt("你猜是什么数字？");
		} else if (guessNumber > number) {
			alert("猜大了！");
			var guessNumber = prompt("你猜是什么数字？");
		}
	} while (guessNumber != number)

	if (parseFloat(guessNumber) == number) {
					alert("恭喜你猜对了！");
				}
```

```js
//改进
	function getRandom(min, max) {
		return Math.floor(Math.random() * (max - min + 1)) + min;
	}
	var number = getRandom(1, 10);

	do {

		var guessNumber = prompt("你猜是什么数字？");
		if (guessNumber < number) {
			alert("猜小了！");

		} else if (guessNumber > number) {
			alert("猜大了！");

		} else {
			alert("恭喜你猜对了！");
			break;
		}

	} while (true)

```

- 10 次机会

```js
	function getRandom(min, max) {
		return Math.floor(Math.random() * (max - min + 1)) + min;
	}
	var number = getRandom(1, 50);

	for (i = 1; i <= 10; i++) {
		var guessNumber = prompt("你猜是什么数字？（1-50之间,10次机会)");
		if (guessNumber < number) {
			alert("猜小了！");

		} else if (guessNumber > number) {
			alert("猜大了！");

		} else {
			alert("恭喜你猜对了！");
			break;
		}
	}
	if (i > 10) {
		alert("机会用完！")

	}
```

### 日期对象
[Date - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

Date() 日期对象 是一个构造函数 必须使用**new实例化**后来调用创建我们的日期对象

- 使用date
```js
var date = new Date();
console.log(date);
```

- 参数常用的写法

数字型 2019,10,61 或者是 ==字符串型== 2019-10-1 8:8:8 （最常用字符串）
	书写格式不一样 `, - :`

```js
var date1 = new Date(2019, 10, 1)；
console. log(date1)；//返回的是 11月不是 10月
var date2 = new Date('2019-10-1 8:8:8'）
console. log(date2);
```

#### 日期格式化

需要获取日期指定的部分，所以我们要手动的得到这种格式。

##### 年月日

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220819172639.png)

[Date.prototype.getFullYear() - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getFullYear)

```js
var moonLanding = new Date();
console.log(moonLanding.getFullYear()); // 2022
console.log(moonLanding.getMonth() + 1); //月份 返回的月份小1个月 记得要+1
console.log(moonLanding.getDate()); //返回的是 几号
console.log(moonLanding.getDay()); // 周一返回的是1 周六返回的是6 但是周日返回的是0


var year = moonLanding.getFullYear();
var month = moonLanding.getMonth() + 1;
var dates = moonLanding.getDate();
var arr = ["星期日", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六"]
console.log("今天是：" + year + "年" + month + "月" + dates + "日" + " " + arr[moonLanding.getDay()])

```

##### 时分秒函数

```js

function time() {
	var moonLanding = new Date();
	var h = moonLanding.getHours();
	h = > 10 ? h : "0" + h;
	var m = moonLanding.getMinutes();
	m = > 10 ? m : "0" + m;
	var s = moonLanding.getSeconds();
	s = > 10 ? s : "0" + s;

	console.log(h + ":" + m + ":" + s);
}

time();
```

补0 ：[[#三元表达式]]


##### 获取日期的**总的**毫秒形式（时间戳）

不是当前时间的毫秒数 而是距离1970年1月1号过了多少毫秒数

Date 对象是基于 1970 年 1 月 1 日（世界标准时间）起的毫秒数，[为什么计算机起始时间丛 1970 年开始？](https://cloud.tencent.com/developer/article/1630408)

我们经常利用总的毫秒数来计算时间，因为它更精确

```js
//1.
var moonLanding = new Date();
console.log(moonLanding.valueOf()); //就是 我们现在时间 距离1970.1.1 总的毫秒数
console.log(moonLanding.getTime());

//2.简单的写法 "+"
var date1 = +new Date();
console.log(date1);

//3.更简单的写法 (h5新增)
console.log(Date.now());
```

##### 案例：倒计时效果

1. 核心算法：输入的时间减去现在的时间就是剩余的时间，即倒计时，但是不能拿着时分秒
相減，比如 05 分减去 25 分，结果会是负数的。

2. 用时间戳来做。用户输入时间总的毫秒数减去现在时间的总的毫秒数，得到的就是剩余时
间的毫秒数。

3. 把剩余时间总的毫秒数转换为天、时、分、秒（时间戳转换为时分秒）
转换公式如下：
```
秒 = 毫秒 / 1000
d = parseInt(总秒数/ 60/60/24)；//计算天数
h = parseInt（总秒数/ 60/60%24)//计算小时
m = parseInt(总秒数/60%60);//计算分数
s = parseInt(总秒数%60)；//计算当前秒数
```

```js
        function countDown(time) {
            var date1 = +new Date(time);
            var nowTime = +new Date();
            var countDown = (date1 - nowTime) / 1000;
            var d = parseInt(countDown / 60 / 60 / 24);
            var h = parseInt(countDown / 60 / 60 % 24);
            h = h > 10 ? h : "0" + h;
            var m = parseInt(countDown / 60 % 60);
            m = m > 10 ? m : "0" + m;
            var s = parseInt(countDown % 60);
            s = s > 10 ? s : "0" + s;
            return (d + "天" + h + ":" + m + ":" + s);
        }
        console.log(countDown("2023-1-1 0:0:0")); 
```

### 数组对象

[Array - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)


#### 数组对象的创建
[[#创建数组]]

创建数组对象的两种方式
	字面量方式
	new Array0

#### 检测是否为数组
1. `instanceof`

```js
var arr = [];
console.log(arr instanceof Array); //ture
```
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220819223415.png)

2. `Array.isArray(参数)`
```js
var arr = [];
console.log(Array.isArray(arr));
```

#### 添加删除数组元素的方法
[[#数组中新增元素]]

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220819235121.png)

`数组.方法();`

##### 末尾新加
`push()` 在我们数组的末尾 添加一个或者多个数组元素 push 推

```js
var arr = [1,2,3];
console.log(arr.push(4)); // [1,2,3,4]
```

push 是可以给数组追加新的元素
push () 参数直接写 数组元素就可以了
push完毕之后，返回的结果是 新数组的长度(length)
原数组也会发生变化

##### 开头新加
`unshift()` 在我们数组的开头 添加一个或者多个数组元素

```js
arr.shift("red");
```

注意同上

##### 筛选数组案例
有一个包含工资的数组[1580，1280，2000，2180，1880]，要求把数组中工资超过2880的删除，剩余的放到新数组里面

```js
	let arr = [1500, 1200, 2000, 2100, 1800];
	let newArr = [];
	for (i = 0; i < arr.length; i++) {
		if (arr[i] <= 2000) {
			newArr.push(arr[i])
		}
	}
	console.log(newArr);
```


#### 数组排序

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820145326.png)

```js
//翻转
        let arr = [1500, 1200, 2000, 2100, 1800];
        arr.reverse();
        console.log(arr);

```

sort 会有问题
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820145831.png)
按照前面的数排序了

```js
//冒泡排序
        let arr = [1500, 1200, 2000, 2100, 1800];
        arr.sort((function (a, b) { //固定写法 记住就行
            return a - b; //a-b升序；b-a降序
        }));
        console.log(arr);
```

#### 数组索引方法

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820150200.png)

```js
        let arr = ["red", "green", "blue", "pink"];
        console.log(arr.indexOf("blue"));
```

- indexOf如果有两个一样的元素，只返回第一个满足条件的索引号（从前往后找）（lastIndexOf从后往前找）
- 如果不存在元素（找不到），则返回-1。

##### 数组去重（重点案例）

有一个数组['c','a','z','a','x','a','x','c','b']，要求去除数组中重复的元素。

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820151755.png)

```js
	let arr = ['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b']
	let newArr = [];
	for (i = 0; i < arr.length; i++) {
		if (newArr.indexOf(arr[i]) == -1) {
			newArr.push(arr[i]);
		} 
	}
	console.log(newArr);
```


#### 数组转换为字符串

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820151957.png)

toString只能逗号
join默认逗号，但是可以加分隔符

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820152151.png)

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820152247.png)




### 字符串对象

#### 基本包装类型
基本包装类型：就是把简单数据类型 包装成为了 复杂数据类型，这样基本数据类型就有了属性和方法。

为了方便操作基本数据类型，JavaScript 还提供了三个特殊的引用类型：String、Number 和 Boolean.

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820152756.png)



#### 字符串的不可变
指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中新开辟了一个内存空间。原来的值还是存在的
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820152947.png)

因为我们字符串的不可变，所以不要大量的拼接字符串，会占用大量内存空间

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820153134.png)

#### 根据字符返回位置
字符串所有的方法，都不会修改字符串本身(字符串是不可变的)，操作完成会返回一个新的字符串。

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820153222.png)
类似数组

`str.indexOf("要查找的字符",[起始的位置])`

```js
let str = "鹅鹅鹅，曲项向天歌";
	console.log(str.indexOf("鹅"))； // 0 起始位置
str.indexOf("鹅",2) // 2 指定位置
```

##### 案例：返回字符位置和次数

查找字符串"abcoefoxyozzopp"中所有 o 出现的位置以及次数

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820161256.png)


```js
	let str = "abcoefoxyozzopp";
	let index = str.indexOf("o");
	let count = 0;
	while (index !== -1) {
		console.log(index);
		count++;
		index = str.indexOf('o', index + 1);
	}
	console.log("o出现的次数" + count)
```

课后作业['red',blue','red','green', 'pink','red']，求 red 出现的位置和次数

#### 根据位置返回字符（重点）

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220820232613.png)


第二个可以判断用户按了哪个键
第三个新增的更简单

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821001359.png)


- 案例：判断最多
判断一个字符串'abcoefoxyozzopp'中出现次数最多的字符，并统计其次数。
[[#判断对象里是否有某个属性]]
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821002102.png)

之前老师讲过调用对象中的属性有两种方法，一种 o. chars，另一种是 o['chars']。
而刚好字符串又自带引号，所以字符串'a'就以 a 的形式存在了对象的属性名中。
这就是为什么 o. chars 不行的原因。

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821011737.png)
```js
	var str = "abdcoefoxyozzopp";
	var o = {}; //搞一个对象
	for (var i =0;i<str.length;i++){
		var chars = str.charAt(i);
		if(o[chars]) {
			o[chars]++ //存在就+1
		} else {
			o[chars] = 1; //不存在就给1
		}
	}
	console.log(o)
```

```js
//遍历对象
	var max = 0;
	var ch = "";
	for (var k in o) {
		if (o[k] > max) {
			max = o[k];
			ch = k
		}
	}
	console.log(max, ch);
```
[[JavaScript#遍历对象属性]]


#### 字符串操作方法
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821012825.png)

后三个 截取字符串

```js
var str1 = "我真的无语"
console.log(str1.substr(3,2)); //无语 //第一个3是索引号，第二个2是截取的字符数
```


#### 替换字符串
`replace('被替换的字','替换为的字符'）`
```js
var str = "andyandy";
console.log(str.replace("a","b")) //bndyandy 只会替换第一个字符
```


#### 字符转换为数组
`split(分隔符)`
[[#数组转换为字符串]] join

```js
var str2 = "red, pink, blue";
console.log(str2.split(","));

var str2 = "red&pink&blue";
console.log(str2.split("&")); //split里的分隔符取决于字符串用什么隔开，如果没有隔开就没法分
```


#### 大小写

```
toUpperCase0 //转换大写
toLowerCase0 //转换小写
```




#### 作业
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821013715.png)

## JavaScript 简单类型与复杂类型
[[#数据类型]]

### 简单类型与复杂类型
简单类型 / 基本数据类型 / 值类型
复杂类型 / 引用类型

值类型：简单数据类型/基本数据类型，在存储时变量中存储的是值本身，因此叫做值类型
string , number, boolean, undefined, null 
	null特殊，其他返回的都是本身，null返回的是一个空的对象 object %%不愧是10天发明的语言%%，如果有个变量我们以后打算存储为对象，暂时没想好放啥，这个时候就给 null

### 堆和栈
堆栈内存空间分配区别：

1. 栈（操作系统）：由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈；
	简单数据类型存放到栈里面

2. 堆（操作系统）：存储复杂类型(对象），一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。
	复杂数据类型存放到堆里面

注意：**JavaScript 中没有堆栈的概念**，通过堆栈的方式，可以让大家更容易理解代码的一些执行方式，便于将来学习其他语言

### 内存分配
- 筒单类型的内存分配
简单数据类型 是存放在栈里面，里面**直接开辟**一个空间，存放的是**值**

- 复杂类型的内存分配
复杂数据类型 首先在**栈**里面存放**地址** 十六进制表示 然后这个**地址指向堆**里面的数据

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821014732.png)


### 传递参数
- 简单类型传参
函数的形参也可以看做是一个变量，当我们把一个值类型变量作为参数传给函数的形参时，其实是把变量**在栈空间里**的值**复制了一份**给形参，那么在方法内部对形参做任何修改，都不会影响到的外部变量。

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821020042.png)

- 复杂类型传参
函数的形参也可以看做是一个变量，当我们把引用类型变量传给形参时，其实是把变量在栈空间里保存的**堆地址复制**给了形参，形参和实参其实保存的是**同一个堆地址**，所以操作的是同一个对象，函数内部改了也会导致外部变量变化。

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821015757.png)
 


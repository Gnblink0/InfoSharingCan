[[前端]]

CSS 一定是和[[HTML]]结合联动的，比如，一个不会动的娃娃你依然可以觉得 ta 像人（不用[[JavaScript]]的静态网页依然可以看），但是一坨没有骨头的肉/一具没有肉的骷髅无论如何都不太像人...

# 正文

课程：[黑马程序员 html5 +css3+前端项目视频教程 - bilibili](https://www.bilibili.com/video/BV1Kg411T7t9?vd_source=edb3b9d2edcf09617c0c07c0499efd40)

⚠️ 以下直接复制粘贴 ob 里的笔记，未做格式化处理，包括一些无法识别的标题链接和内链图片


## 基础认知
目标：理解 CSS 的作用，了解 CSS语法规则，知道 CSS 的引入方式及其区别

学习路径：
1. CSS初识
2. CSS引入方式

### 什么是 CSS？
CSS 指层叠样式表 (**C**ascading **S**tyle **S**heets)

CSS作用是什么？
-   样式定义**如何显示** [[HTML]] 元素，CSS 同时控制多重网页的样式和布局。
-   样式通常存储在**样式表**中，**外部样式表**通常存储在 **CSS 文件**中，外部样式表可以极大提高工作效率
-   多个样式定义可**层叠**为一个


注意点：
1. CSS 标点符号都是英文状态下的
2. 每一个样式键值对写完之后，最后需要写分号

### CSS 引入方式（写在哪里？）
内嵌式：CSS 写在style标签中
提示：style标签虽然可以写在页面任意位置，但是通常约定写在【head标签里面，title标签下面】

==外联式==：CSS 写在一个单独的. css 文件中
提示：需要通过link标签在网页中引入（link标签同样写在 【head标签里面，title标签下面】）

行内式：CSS写在标签的style属性中
提示：基础班不推荐使用，之后会配合 js 使用

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220621211155.png)



### css 三大特性
目标：能够认识 CSS 的继承 和层叠 特性，会计算 CSS 的优先级权重的比较

学习路径：
1. 继承性
2. 层叠性
3. 优先级

#### 继承性
特性：子元素有默认继承父元素样式的特点（子承父业）

可以继承的常见属性：
1. color
2. font-style、 font-weight、 font-size、 font-family
3. text-indent. text-align
4. line-height

注意点：
可以通过[[浏览器开发者工具|调试工具]]判断样式是否可以继承 `inherited from`
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220623211020.png)


##### 继承的应用

好处：可以在一定程度上减少代码

常见应用场景：
1. 可以直接给u设置 list-style:none 属性，从而去除列表默认的小圆点样式
2. 直接给body标签设置统一的font-size，从而统一不同浏览器默认文字大小

##### 继承失效的特殊情况
如果元素有浏览器默认样式，此时继承性依然存在，但是优先显示浏览器的默认样式
1. a标签的color会继承失效
2. h系列标签的font-size会继承失效
3. div 的高度不能继承，但是宽度有类似于继承的效果%%但是实际上不是继承得来的 而是本身默认会独占一行%%

#### 层叠性
CSS (Cascading style sheets) 层叠样式表，所谓的层叠即叠加的意思，表示样式可以一层一层的层叠覆盖

1. 给同一个标签设置不同的样式 一此时样式会层叠叠加 一 会共同作用在标签上
2. 给同一个标签设置相同的样式 一此时样式会层叠覆盖一最终写在最后的样式会生效
	问题：给同一个标签设置了相同的样式，此时浏览器会如何渲染呢？
	结果：如果给同一个标签设置了相同的属性，此时样式会==层叠（覆盖）==，写在最下面的会生效

注意点：
1. 当样式冲突时，只有当选择器优先级相同时，才能通过层叠性判断结果


#### 优先级
能够计算 CSS 权重，分析井解决 CSS 冲突问题

特性：不同选择器具有不同的优先级，优先级高的选择器样式会覆盖优先级低选择器样式

优先级公式：
继承＜通配符选择器＜标签选择器＜类选择器＜id 选择器 ＜行内样式＜ ! important
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220707092144.png)

!important = 开挂
1. !important写在属性值的后面，分号的前面！
2. !important不能提升继承的优先级，只要是继承 优先级就是最低
3. 实际开发中不建议使用 !important

```css
p {
color:purple !important;
}
```

##### 权重叠加计算
场景：如果是[[#选择器进阶|复合选择器]]，此时需要通过权重叠加计算方法，判断最终哪个选择器优先级最高会生效

权重叠加计算公式：（每一级之间不存在进位）
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220623213731.png)

比较规则：
1. 先比较第一级数字，如果比较出来了，之后的统统不看
2. 如果第一级数字相同，此时再去比较第二级数字，如果比较出来了，之后的统统不看
3. 如果最终所有数字都相同，表示==优先级相同，则比较层叠性==（谁写在下面，谁说了算！）

注意点：!important如果不是继承，则权重最高，天下第一！

![[Pasted image 20220623213915.png]]

权重计算题解题步骤：
1. 先判断选择器是否能直接选中一个确定的标签，如果不能直接选中→是继承，优先级最低→直接 pass
	如果都是继承？转而分析它父级标签的颜色
2. 通过权重计算公式，判断谁权重最高
3. 如果权重相同（最终所有数字都相同），表示优先级相同，则比较层叠性

注意点：
实际开发中选择选择标签需要精准，尽量避免多个选择器同时选中一个标签的情况，不要自己难为自己


### css 书写顺序

从上到下
1. 浮动 / display ：float
2. 盒子模型：margin border padding 宽度高度背景色
3. 文字样式

便于阅读，优化处理，浏览器执行效率更高

写的时候先写宽高背景色，可视化

## CSS语法
![Eg3uF9scAT5zQ1M|500](https://s2.loli.net/2022/03/16/Eg3uF9scAT5zQ1M.jpg)
CSS 规则由两个主要的部分构成：
- 选择器
	- 选择器通常是您需要改变样式的 HTML 元素
- 一条或多条声明
	- 每条声明由一个属性和一个值组成
		- 属性和值被冒号分开
		- 属性（property）是您希望设置的样式属性（style attribute）
		- 每个属性有一个值

声明总是以分号 ` ; ` 结束，以大括号 ` {} ` 括起来
 `p {color:red;text-align:center;}`

为了让CSS可读性更强，可以每行只描述一个属性
``` css
p
{
    color:red;
    text-align:center;
}
```

### 注释
CSS注释以 `/*` 开始, 以 `*/ ` 结束

```
/*这是个注释*/
p
{
    text-align:center;
    /*这是另一个注释*/
    color:black;
    font-family:arial;
}
```


## 选择器
目标：理解选择器的作用，能够使用基础选择器在 HTML 中选择元素

学习路径：
1. 标签选择器
2. 类选择器
3. id选择器
4. 通配符选择器

选择器的作用：
选择页面中对应的标签（找她），方便后续设置样式（改她）


### 标签选择器
结构：标签名 {css属性名：属性值；}

作用：通过标签名，找到页面中所有这类标签，设置样式

注意点：
1. 标签选择器选择的是一类标签，而不是单独某一个
2. 标签选择器无论嵌套关系有多深，都能找到对应的标签（套娃躲猫猫）


### 类选择器（.）
结构：.类名{css属性名：属性值；}%%.（点）开头%%

作用：通过类名，找到页面中所有带有这个类名的标签，设置样式

注意点：
1. 所有标签上都有class属性，class属性的属性值称为类名（类似于名字）
2. 类名可以由数字、字母、下划线、中划线组成，但不能以数字或者中划线开头
3. 一个标签可以同时有多个类名，类名之间以空格隔开
4. 类名可以重复，一个类选择器可以同时选中多个标签
%%「类」类似名字，可以重复%%


### id选择器（#）
结构：#id属性值{css属性名：属性值；}%%#开头%%

作用：通过 id 属性值，找到页面中带有这个 id 属性值的标签，设置样式

注意点：
1. 所有标签上都有id属性
2. id属性值类似于身份证号码，在一个页面中是唯一的，不可重复的！
3. 一个标签上只能与一个id属性值
4. 一个id选择器只能选中一个标签

%%「id」类似身份证号，不能重复%%

实际开发的情况：

类选择器用的最多

id 一般配合 js 使用，除非特殊情况，否则不要使用 id 设置样式

实际开发中会遇到冗余代码的抽取（可以将一些公共的代码抽取到一个公共的类中去）


### 通配符选择器(`*`)
结构：`*{css属性名：属性值；}`
作用：找到页面中所有的标签，设置样式
注意点：
1. 开发中使用极少，只会在极特殊情况下才会用到
2. 在基础班小页面中可能会用于去除标签默认的margin和padding（后续讲解）



目标：能够理解复合选择器的规则，并使用复合选择器在 HTML 中定位元素

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220623193230.png)

### 复合选择器
#### 后代选择器：` `
作用：根据 HTML 标签的嵌套关系，选择父元素 后代中 满足条件的元素
选择器语法：选择器 1 ` ` 选择器 2 {css}

结果：在选择器 1 所找到标签的后代（儿子、孙子、重孙子…）中，找到满足选择器 2 的标签，设置样式

注意点：
1. 后代包括：儿子、孙子、重孙子…(被父包裹的全部都会被选中)
2. 后代选择器中，选择器与选择器之前通过 空格 隔开

#### 子代选择器：`＞`
作用：根据 HTML 标签的嵌套关系，选择父元素 子代中 满足条件的元素%%子代和后代不一样，子代只包含儿子，不包含孙子等等  %%
选择器语法：选择器1＞选择器2{ css }
结果：在选择器1所找到标签的子代（儿子）中，找到满足选择器2的标签，设置样式
注意点：
1. 子代只包括：儿子
2. 子代选择器中，选择器与选择器之前通过＞隔开

### 交并集选择器
#### 并集选择器：`，`
作用：同时选择多组标签，设置相同的样式
选择器语法：选择器1，选择器2 { css }
结果：
找到选择器1 和选择器2 选中的标签，设置样式
注意点：
1. 并集选择器中的每组选择器之间通过`，`分隔
2. 并集选择器中的每组选择器可以是基础选择器或者复合选择器
3. 并集选择器中的每组选择器通常一行写一个，提高代码的可读性


#### 交集选择器：紧挨
作用：选中页面中 同时满足 多个选择器的标签
选择器语法：选择器1选择器2 { css
结果：
(既又原则）找到页面中 既 能被选择器1选中，又能被选择器2选中的标签，设置样式
注意点：
1. 交集选择器中的选择器之间是紧挨着的，没有东西分隔
2. 交集选择器中如果有标签选择器，标签选择器必须写在最前面


### emmet语法
4.1 emmet语法
作用：通过简写语法，快速生成代码
语法：类似于刚刚学习的选择器的写法

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220623192318.png)
写表格非常方便：`table>tr*5>td*6`

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821031658.png)
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821031713.png)


### 伪类选择器
#### hover伪类选择器
作用：选中鼠标悬停在元素上的状态，设置样式
选择器语法：`选择器：hover {css}`

伪类选择器选中的元素的某种状态 冒号

#### 结构伪类选择器
[[#浮动]]

1. 作用与优势：
	1. 作用：根据元素在**HTML中的结构关系**查找元素
	2. 优势：减少对于HTML中类的依赖，有利于保持代码整洁%%可以按顺序检索，不用一个一个取类名打上标签来检索%%
	3. 场景：常用于查找某父级选择器中的子元素

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821025646.png)


2. 选择器
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220628223950.png)

##### :nth-child
1. n 为：0、 1、 2、 3、4、 5、 6 %%类似 python 里的顺序，从 0 开始%%

2. 通过 n 可以组成常见公式 （必须以 n 开始，所以不能写成 `1-n`）

``` css
li:nth-child(2n) {
background-color: green;
}
```

不用背公式，一般只会用到偶数、奇数、几的倍数（4n）
![[Pasted image 20220707000437.png]]
%%能不能找一个区间里的？%%


##### :nth-of-type
![[Pasted image 20220707001637.png]]

区别：
:nth-child ——直接在所有孩子中数个数
:nth-of-type ——先通过该 类型 找到符合的一堆子元素，然后在这一堆子元素中数个数



## 字体和文本样式
目标：能够使用字体和文本相关样式修改元素外观样式
学习路径：
1. 字体样式
	1. 字体大小：font-size
	2. 字体粗细：font-weight
	3. 字体样式：font-style
	4. 字体类型：font-family
	5. 字体类型：font屈性连写
2. 文本样式
3. line-height行高


### 字体大小
属性名：font-size
取值：数字+ px
注意点：
	谷歌浏览器默认文字大小是16px
	单位需要设置，否则无效

#### 字号单位
字号有很多种单位：px像素，pt磅和em相对字体大小
```css
.cm-header-1 {
  font-size: 2em;
}
.cm-header-2 {
  font-size: 18px;
}
.cm-header-3 {
  font-size: 20pt;
}
```

1em = 当前标签的 font-size 的大小

### 字体粗细
属性名：font-weight
取值：
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220621224756.png)

注意点：
不是所有字体都提供了九种粗细，因此部分取值页面中无变化
实际开发中以：正常、加粗两种取值使用最多。
整百数不用带单位



### 字体样式（是否倾斜）
属性名：font-style
取值：
正常（默认值）：normal
倾斜：italic

### 字体类型
1.4 常见字体系列（了解）

无衬线字体 (sans-serif)
	1. 特点：文字笔画粗细均匀，并且首尾无装饰
	2. 场景：网页中大多采用无衬线字体
	3. 常见该系列字体：黑体、Arial

衬线字体 (serif)
	1. 特点：文字笔画粗细不均，并且首尾有笔锋装饰
	2. 场景：报刊书籍中应用广泛
	3. 常见该系列字体：宋体、Times New Roman

等宽字体 (monospace)
	1. 特点：每个字母或文字的宽度相等
	2. 场景：一般用于程序代码编写，有利于代码的阅读和编写
	3. 常见该系列字体：Consolas. fira code

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220621225318.png)

1.5 字体系列 font-family
属性名：font-family
常见取值：具体字体1,具体字体2,具体字体3,具体字体4,==字体系列==%%兜底%%
	具体字体："Microsoft YaHei"、微软雅黑、黑体、宋体、楷体等….
	字体系列：sans-serif、 serif、monospace等…

渲染规则：
1. 从左往右按照顺序查找，如果电脑中未安装该字体，则显示下一个字体
2. 如果都不支持，此时会根据操作系统，显示最后字体系列的默认字体

注意点：
1. 如果字体名称中存在多个单词，推荐使用引号包裏
2. 最后一项字体系列不需要引号包裹
3. 网页开发时，尽量使用系统常见自带字体，保证不同用户浏览网页都可以正确显示



### 字体font相关属性的连写
属性名：font
取值：
font: style weight size family;
顺序要求：swsf (style weight size family)（稍微舒服）
省略要求：只能省略前两个，如果省略了相当于设置了默认值

注意点：如果需要同时设置单独和连写形式，单独的不能写在连写前面，会被默认覆盖


### 文本缩进
属性名：text-indent
取值：
	数字+ px
	数字+em（推荐：1em = 当前标签的font-size的大小）

### 文本水平对齐方式
属性名：text-align
取值：
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220622100926.png)
注意点：
如果需要让文本水平居中，text-align属性给文本所在标签（文本的父元素）设置


大容器包裹内容：叫做大盒子，一般用 `div` 表示

#### 水平居中方法总结 text-align: center
text-align : center 能让那些元素水平居中？
1. 文本
2. span标签、a标签
3. input标签、img标签

注意点：
1. 如果需要让以上元素水平居中，text-align:center 需要给以上元素的 ==父元素== 设置%%也就是都给div盒子设置%%

#### 水平居中方法总结 margin: 0 auto
如果需要让div、p、h（大盒子）水平居中？
可以通过`margin:0 auto；`实现%%一个固定写法，上下为0，左右自动适应%%

注意点：
1. 如果需要让 div、 p、h（大盒子）水平居中，直接给 ==当前元素本身== 设置即可
2. margin: 0 auto 一般针对于固定宽度的盒子，如果大盒子没有设置宽度，此时会默认占满父元素的宽度，就失去了作用

![[CSS#子绝父相水平居中案例]]

### 文本修饰线
属性名：text-decoration
取值：
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220622101737.png)

注意点：
开发中会使用 text-decoration: none；清除[[HTML#链接标签（a）| a 标签]]默认的下划线

### 行高
作用：控制行间距（给一行上下增加间距）
属性名：line-height

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220622103027.png)
原理：行高=文本高度+上下间距（等分）

取值：
数字+px
倍数（当前标签font-size的倍数）

应用：
1. 让<font color=#F36208>单行文本</font>垂直居中可以设置<font color=#F36208> line-height:文字父元素高度</font>
2. 网页精准布局时，会设置<font color=#F36208> line-height:1</font>可以取消浏览器自动设置的上下间距%%让文字紧贴%%
3. 行高与font连写的注意点：
如果同时设置了行高和font连写，注意覆盖问题
`font: style weight size/line-height family;`


## 背景相关属性
二、背景相关属性
目标：能够使用 背景相关属性 装饰元素样式
学习路径：
1. 背景颜色
2. 背景图片
3. 背景平铺
4. 背景位置
5. 背景相关属性连写

### 背景颜色
属性名：background-color (bgc)
属性值：[[#颜色的常见取值|颜色取值]]：关键字、rgb表示法、rgba表示法、十六进制…

注意点：
背景颜色默认值是透明：rgba(0,0,0,0)、transparent
背景颜色不会影响盒子大小，并且还能看清盒子的大小和位置，一般在布局中会习惯先给盒子设置背景颜色

### 背景图片
属性名：background-image (bgi)
属性值：background-image：url('图片的路径'）

注意点：
背景图片中url中可以省略引号
背景图片默认是在水平和垂直方向平铺的（铺瓷砖）
背景图片仅仅是指给盒子起到装饰效果，类似于背景颜色，是不能撑开盒子的


### 背景平铺
属性名：background-repeat (bgr)
属性值：
`background-repeat: no-repeat;
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220623194335.png)

### 背景位置
属性名：background-position (bgp)
属性值：`background-position:水平方向位置 垂直方向位置;`
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220623194556.png)

注意点：方位名词取值和坐标取值可以混使用，第一个取值表示水平，第二个取值表示垂直

![[CSS#^ico3n6]]

### 背景图片大小
作用：设置背景图片的大小
语法：`background-size：宽度 高度；`
取值：
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825143613.png)
工作中一般盒子图片是等比例的，contain 和 cover 没有区别


### 背景相关属性的连写形式
属性名：background (bg)
属性值：单个属性值的合写，取值之间以空格隔开
书写顺序：（比较宽松 都可以）推荐：background: color image repeat position/size
省略问题：
	可以按照需求省略
	特殊情況：在 pc 端，如果盒子大小和背景图片大小一样，此时可以直接写 `background: url()`

background-size一般单独拆开写

### 拓展 img标签和背景图片的区别
需求：需要在网页中展示一张图片的效果？
方法一：直接写上img标签即可
img标签是一个标签，不设置宽高默认会以原尺寸显示
方法二：div标签 + 背景图片
需要设置div的宽高，因为背景图片只是装饰的CSS样式，不能撑开div标签

## 图片
### 图片居中
上下居中
`vertical-align:middle` (调节图片垂直对齐方式)

## 盒子模型
目标：能够认识 盒子模型的组成，能够掌握盒子模型边框、内边距、外边距的 设置方法

学习路径：
1. 盒子模型的介绍
2. 内容区域的宽度和高度
3. 边框( border）
4. 内边距( padding)
5. 外边距 (margin)

⚠️ 必写
```css
*{
	margin:0;
	padding:0;
}
```

### 盒子模型的介绍
1. 盒子的概念
	1. 页面中的每一个标签，都可看做是一个 "盒子〞，通过盒子的视角更方便的进行布局
	2. 浏览器在渲染（显示）网页时，会将网页中的元素看做是一个个的矩形区域，我们也形象的称之为 盒子
2. 盒子模型
CSS中规定每个盒子分别由：内容区域 (content) 内边距区域 (padding)、边框区域 (border） 外边距区域（margin） 构成，这就是盒子模型

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220627094449.png)



### 边框 (border）
#### 单个属性
作用：给设置边框粗细、边框样式、边框颜色效果
单个属性：
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220627094705.png)

border-style 必须要写 否则无法显示

#### 连写形式
属性名：border
属性值：单个取值的连写，取值之间以空格隔开，如：border:10px solid red;
快捷键：bd + tab

#### 单方向边框
场景：只给盒子的某个方向单独设置边框
属性名：border -方位名词
属性值：连写的取值

### padding
4.1 内边距 (padding)-取值
作用：设置边框 与 内容区域 之间的距离
属性名：padding
常见取值：
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220627103704.png)
记忆规则：从上开始赋值，然后顺时针赋值，如果设置赋值的，看对面的！



### 盒子大小
#### 内容的宽度和高度
作用：利用 width 和 height 属性默认设置是盒子 内容区域 的大小
属性：width / height
常见取值：数字+px



#### 盒子实际大小（内减）

当盒子被撑大后%%因为width height属性设置的是contend的大小%%，如何满足需求？

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220627103902.png)

![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220707093033.png)

#### 不会撑大盒子的特殊情况（块级元素）
如果子盒子没有设置宽度，此时宽度默认是父盒子的宽度
此时给子盒子设置左右的 padding 或者左右的 border，此时不会撑大子盒子

#### CSS3盒模型（自动内减）
需求：盒子尺寸 `300*300`，背景粉色，边框 10px 实线黑色，上下左右 20px 的内边距，如何完成？

解决方法 ①：手动内减
	操作：自己计算多余大小，手动在内容中减去
	缺点：项目中计算量太大，很麻烦

解决方法 ②：自动内减
	操作：给盒子设置属性 `box-sizing : border-box；`即可
	优点：浏览器会自动计算多余大小，自动在内容中减去


CSS3盒模型
属性名：box-sizing
属性值：border-box
即 `box-sizing:border-box;`

### 外边距 （margin） 
#### 取值
作用：设置边框以外，盒子与盒子之间的距离
属性名：margin
常见取值：
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220627112619.png)
记忆规则：从上开始赋值，然后顺时针赋值，如果设置赋值的，看对面的！

#### 单方向设置
场景：只给盒子的某个方向单独设置外边距
属性名：margin-方位名词
属性值：数字 + px

margin 单方向设置的应用
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220627112811.png)

#### 正常情况
场景：水平布局 的盒子，左右的margin正常，互不影响
结果：最终两者距离为左右 margin 的和

#### 外边距折叠现象
##### ① 合并现象
场景：**垂直**布局 的块级元素，上下的margin会**合并** %%噢 实际也碰到过%%
结果：最终两者距离为 margin 的最大值
%%比喻，两个盒子的腿互踹，只有长的那个才能踹到对面的%%
解决方法：避免就好，只给其中一个盒子设置margin即可

##### ② 塌陷现象
场景：互相嵌套 的块级元素，子元素的 margin-top 会作用在父元素上
结果：导致父元素一起往下移动（坑爹、拉爹下水）
因为：两者的 margin 贴在一起之后会自动合并


解决方法：
1. 给父元素设置border-top 或者 padding-top （分隔父子元素的margin-top)
2. 给父元素设置overflow: hidden
3. 转换成行内块元素
4. 设置浮动 [[CSS#双伪元素清除法]]


#### 版心居中
[[#水平居中方法总结 margin 0 auto]]
版心：网页的有效内容
版心一般100%都是居中的

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821023008.png)

### 清除默认内外边距
场景：浏览器会默认给部分标签设置默认的 margin 和 padding
	比如：body标签默认有margin：8px
	比如：p标签默认有上下的margin
	比如：u标签默认由上下的margin和padding-left
但一般在项目开始前需要先清除这些标签默认的margin和padding，后续自己设置

解决方法：
[[#通配符选择器]]
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220627113030.png)

### 行内元素的margin和padding无效情况
场景：给行内元素设置margin和padding时
结果：
1. 水平方向的margin和padding布局中有效！
2. 垂直方向的 margin 和 padding 布局中无效！

## 浮 动
之前学的是把盒子造出来，浮动是把盒子摆到对应的位置上去

- [[#结构伪类选择器]]
- [[#伪元素|伪元素]]
- [[#标准流|标准流]]
- [[#浮动|浮动]]
- [[#清除浮动|清除浮动]]


### 伪元素 
%%原来是这样的。 。我get到了，ob里用了很多这个，比如图标、引用引号，还有我现在有的这个注释对话泡泡%%
目标：能够使用 伪元素 在网页中创建内容
伪元素：一般页面中的非主体内容可以使用伪元素

区别：
1. 元素：HTML 设置的标签
2. 伪元素：由 CSS模拟出的标签效果

种类：
![[Pasted image 20220707002135.png]]

注意点：
1. 必须设置 content 属性才能生效
2. 伪元素默认是[[HTML#行内元素|行内元素]]


### 标准流
标准流：又称文档流，是浏览器在渲染显示网页内容时默认采用的一套排版规则，规定了应该以何种方式排列元素

常见标准流排版规则：
1. [[HTML#块级元素|块级元素]]：从上往下，垂直布局，独占一行
2. [[HTML#行内元素|行内元素]] 或 [[HTML#行内块元素|行内块元素]]：从左往右，水平布局，空间不够自动折行

### 浮动
目标：能够认识使用 浮动的作用，了解 浮动的特点

学习路径：
1. 浮动的作用
2.浮动的代码
3. 浮动的特点
4. 浮动的案例

#### 作用

浮动可以使元素脱标（脱离标准流）

- 早期的作用：图文环绕

- 现在的作用：网页布局
场景：让垂直布局的盒子变成水平布局（让块级标签**完美地在一行排列**）
	让垂直的变水平还可以用[[HTML#行内块元素]]，但是换行两个盒子间会产生一个空格的空隙，很麻烦，可读性很差


#### 代码
属性名：float
属性值：
	left 左浮动
	right 右浮动

`float: left；`

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821032932.png)

#### 特点
1. 浮动元素会脱离[[#标准流|标准流]]（简称：脱标），在标准流中不占位置
	相当于从地面飘到了空中%%直接升维……但是也有水平标准流啊？%%
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821033319.png)
2. 浮动元素比标准流高半个级别，可以覆盖标准流中的元素

3. 浮动找浮动，下一个浮动元素会在 上一个浮动元素后 左右浮动%%飞到天上也要排队哈哈哈哈%%

4. 浮动元素会受到上面元素边界的影响，顶对齐 %%为什么浮动不飘到最上面，而只是水平飘？因为上面有天花板（块元素独占一行）%%

5. 浮动元素有特殊的显示效果（浮动拥有行内块特点）
	一行可以显示多个
	可以设置宽高

注意点：
浮动的元素不能通过 text-align: center 或者 margin: 0 auto，让浮动元素本身[[#水平居中方法总结 margin 0 auto|水平居中]]
但是里面的内容还是可以水平居中

#### 案例
- 1个大盒子（因为要版心居中）套2个浮动的div标签
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821033936.png)


- 小米模块
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821170047.png)
删掉绿和粉即为最终效果

```html
<style>
    * {
        margin: 0;
        padding: 0;
    }

    .box {
        margin: 0 auto;

        width: 1226px;
        height: 614px;
        background: pink;
    }

    .left {
        float: left;

        width: 234px;
        height: 614px;
        background: #800080;
    }

    .right {
        float: right;

        width: 978px;
        height: 614px;
        background-color: green;

    }

    .block {
        float: left;
        width: 234px;
        height: 300px;
        background: #87ceeb;

        margin: 0 14px 14px 0;
    }

    .block:nth-child(4n) { /*⚠️清除第4、8块的右侧margin，否则会放不下（如果父级宽度不够，子级会自动换行 */
        margin: 0;
    }
</style>

<body>
    <div class="box">
        <div class="left">

        </div>
        <div class="right">
            <div class="block"></div>
            <div class="block"></div>
            <div class="block"></div>
            <div class="block"></div>
            <div class="block"></div>
            <div class="block"></div>
            <div class="block"></div>
            <div class="block"></div>
        </div>
    </div>
</body>
```


- 网页导航案例

做网站的主导航必须 li 套 a（一个套一个），只有a的话浏览器会嫌弃，解析效率会很低

宽高给 a 还是给 li？ 看需求
	如果只是文字能点击跳转，给li；如果整个框都能点击跳转，给a（一般都是给a，触发点越大越好）

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821172358.png)

```html
<style>
    * {
        margin: 0;
        padding: 0;
    }

    .nav {
        margin: 0 auto;

        width: 640px;
        height: 50px;
        background-color: #ffc0cb;
    }

    li {
        list-style: none;
    }

    .nav li a {
        float: left;

        width: 80px;
        height: 50px;
        background-color: #ffc0cb;

        font-size: 16px;
        color: white;
        text-decoration: none;
        text-align: center;
        line-height: 50px;
    }

    .nav li a:hover {
        background-color: #008000;
    }
</style>

<body>
    <div class="nav">
        <ul>
            <li><a href="">新闻</a></li>
            <li><a href="">新闻</a></li>
            <li><a href="">新闻</a></li>
            <li><a href="">新闻</a></li>
            <li><a href="">新闻</a></li>
            <li><a href="">新闻</a></li>
            <li><a href="">新闻</a></li>
            <li><a href="">新闻</a></li>
        </ul>
    </div>
</body>


```

### 清除浮动
（辅助）

含义：清除浮动给别的标签带来的影响（没有影响就不用清除）

父子级标签，子级浮动，父级没有高度，后面的标准流盒子会受影响，显示到上面的位置
	影响：如果子元素浮动了，此时**子元素不能撑开**标准流的块级父元素
	原因：子元素浮动后脱标 → 不占位置
	目的：需要父元素有高度，从而不影响其他网页元素的布局

#### 清除浮动的方法

##### 直接设置父元素高度（加高）

优点：简单粗暴，方便
缺点：有些布局中不能固定父元素高度。如：新闻列表、京东推荐模块
	1. 内容可能会变多，盒子可能会增长，但是高度是固定不变的 2. 网页内容特别多的时候也不加固定高

##### 额外标签法

操作：
1. 在父元素内容的最后添加一个块级元素
2. 给添加的块级元素设置 clear:both %%clear:left(right)可以分别清除左右，both就是都清除%%
`<div class="clearfix"></div>` 固定写法

特点：
缺点：会在页面中添加额外的标签，会让页面的HTML结构变得复杂

##### 单伪元素清除法

操作：用伪元素替代了额外标签

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821173905.png)

优点：项目（工作）中经常使用，直接给标签加类即可清除浮动（不用背，规范化写法，每个项目都需要清楚浮动，所以是准备工作时候就直接复制粘贴进去好了的）

补充写法是为了解决兼容性，有些浏览器会给一个小高（高版本都没有这个问题，ie 前端之瘤-.-）
	不用加补充代码了，没有兼容性一说了，因为IE浏览器在2022年6月15日开始淘汰了


##### 双伪元素清除法
[[#外边距折叠现象]]：外边距塌陷：父子标签，都是**块级**，子级加 margin 会影响父级的位置
	转成table就没问题了

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821180611.png)

##### 给父元素设置overflow:hidden

操作：
1. 直接给父元素设置 overflow: hidden

优点：方便 


## 定位

目标：能够说出 定位 的常见应用场景，并且能够说出 不同定位方式 的特点

学习路径：
1. 定位的基本介绍
2. 定位的基本使用
3. 静态定位
4. 相对定位
5. 绝对定位
6. 子绝父相
7. 固定定位
8. 元素的层级关系

### 定位的作用
两个标签叠在一起显示

#### 网页常见布局方式
1. 标准流
	1. 块级元素独占一行 一 垂直布局
	2. 行内元素/行内块元素一行显示多个 一 水平布局
2. 浮动
	1. 可以让原本垂直布局的 块级元素变成水平布局
3. 定位
	1. 可以让元素自由的摆放在网页的任意位置
	2. 一般用于 盒子之间的层叠情况

#### 定位的常见应用场景

1. 可以解决盒子与盒子之间的层叠问题
	定位之后的元素层级最高，可以层叠在其他盒子上面

2. 可以让盒子始终固定在屏幕中的某个位置(搜索栏和logo位于最顶)


### 使用定位的步骤

#### 设置定位方式
属性名：position
常见属性值：
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823162831.png)

#### 设置偏移值
偏移值设置分为两个方向，水平和垂直方向各选一个使用即可
如果 left 和 right 都有，以 left 为准；top 和 bottom 都有以 top 为准

选取的原则一般是就近原则（离哪边近用哪个）

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823162936.png)


#### 相对定位

介绍：自恋型定位，相对于自己之前的位置进行移动
代码：`position:relative;`

```css
.box {
	position:relative;
	left:100px;
	top:200px;
}
```

特点：
1. 需要配合方位属性实现移动
2. 相对于自己原来位置进行移动
3. 在页面中占位置——没有脱标（虽然走了，但是地盘还是我的）
4. 不会让标签具备其他显示模式，仍然具体标签原有的显示模式特点（还是独占一行）

应用场景：
1. 配合绝对定位组CP（子绝父相）
2. 用于小范围的移动


#### 绝对定位

介绍：拼爹型定位，相对于非静态定位的父元素进行定位移动
	先找已经定位的父级，如果有这样的父级就以这个父级为参照物进行定位
		工作中，一般会给父级加relative 相对定位 [[#子绝父相]]
	有父级，但父级没有定位，以浏览器窗口为参照为进行定位（有时候浏览器有默认 padding 用这个定位 0 会取消默认定位 直接移动到贴边）
	![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823171643.png)

代码：`position :absolute;`

特点：
1. 需要配合方位属性实现移动
2. 默认相对于浏览器可视区域进行移动
3. 在页面中不占位置——已经脱标 不占位置（run 了 run 了）
4. 改变标签的显示模式特点：具体行内块特点（在一行共存，宽高生效，如果没有宽度也没有内容，盒子的宽度尺寸就是0） ^r7le9z

应用场景：
1. 配合绝对定位组CP（子绝父相）


#### 子绝父相


父级相对定位；子级绝对定位 —— 子绝父相

父级是广义的父级，父级的父级也可以，逐层查找最近的

##### 子绝父相水平居中案例

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823222722.png)


盒子加了 absolute 之后 margin: 0 auto 会失效
```
position: absolute
left: 50% 
```

盒子的最左边会移到浏览器界面正中（盒子位于中间偏右）

还要往左才能让中心正中
```
position: absolute
left: 50% 
margin-left: -150px
```
再给同方向margin，数值为 负 盒子的宽度一半

垂直居中同理

---
%%产品经理订需求%% 
```
position: absolute
left: 50% 
top: 50%
transform: translate (-50%,-50%)
```
不用自己算一半了，自动改

(案例）导航二维码居中定位案例
需求：根据设计图，在 day06-作业-微金所导航案例 基础上，定位二维码图片完成一致的效果

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823225326.png)
mask 遮罩

![[CSS#^r7le9z]]


#### 固定定位

介绍：死心眼型定位，相对于浏览器进行定位移动
代码：`position:fixed；`

特点：
1. 需要配合方位属性实现移动
2. 相对于浏览器可视区域进行移动 改变位罝参考浏览器窗口
3. 在页面中不占位置一已经脱标
4. 具备行内块特点

应用场景：
1. 让盒子固定在屏幕中的某个位置（顶部搜索、logo等，滚动时永远位于顶部）



#### 元素的层级关系

不同布局方式元素的层级关系：标准流＜ 浮动＜定位

不同定位之间的层级关系：
相对、绝对、固定默认层级相同
此时HTML中写在下面的元素层级更高，会覆盖上面的元素（后来者居上）

- z-index
如果不想改html位置，却还要让前面的标签居上，可以用一个属性
z-index：整数；取值越大，显示顺序越靠上（没有别的的话，取1就行，因为默认值是0）
%%必须要配合position定位才能生效%%


## 装饰
目标：能够完成元素的装饰效果

学习路径：
1. 垂直对齐方式
2. 光标类型
3. 边框圆角
4. overflow溢出部分显示效果
5. 元素本身隐藏

### 垂直对齐方式
#### 认识基线（了解）
基线：浏览器文字类型元素排版中存在用于对齐的基线 (baseline)

![|200](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823230811.png)

浏览器处理行内和行内块标签时，默认按照文字特点解析（都按照文字处理），所以会按基线对齐，导致视觉上不对齐
	所以解决办法有两种：加vertical 和 把标签变为block属性`display: block`


#### 文字对齐问题
场景：解决行内/行内块元素垂直对齐问题
问题：当图片和文字在一行中显示时，其实底部不是对齐的

属性名：vertical-align
属性值：
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823231007.png)

学成在线 [[#用户区域]]用过


### 光标类型

场景：设置鼠标光标在元素上时显示的样式
属性名：cursor
常见属性值：
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823232214.png)

有手的不一定能点

### 边框圆角

场景：让盒子四个角变得圆润，增加页面细节，提升用户体验
属性名：border-radius
常见取值：数字+px、百分比

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823235055.png)

赋值规则：从左上角开始赋值，然后顺时针赋值，没有赋值的看对角！

[Border Radius CSS Generator | CSSmatic](https://www.cssmatic.com/border-radius)

#### 边框圆角的常见应用
- 画一个正圆
	eg 用户头像
1. 盒子必须是正方形
2. 设置边框圆角为盒子宽高的一半  `border-radius:50%`


- 胶囊按钮：
1. 盒子要求是长方形
2. 设置一Horder-radius: 盒子高度的一半

### overflow溢出部分显示效果

溢出部分：指的是盒子 内容部分 所超出盒子范围的区域
场景：控制内容溢出部分的显示效果，如：显示、隐藏、滚动条…
属性名：overflow
常见属性值：
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823235623.png)

滚动一般用得不多（eg b站选集）

### 元素本身隐藏

场景：让某元素本身在屏幕中不可见。如：鼠标hover之后元素隐藏（eg 子菜单）

常见属性：
1. visibility: hidden（一般不常用；因为没脱标，还会占位）
2. display: none（常用这个；不占位隐藏）

```
nav 1i a:hover img{
display: block；
}
```

hover 的是 a，显示的是 img



### (拓展）元素整体透明度
场景：让某元素整体（包括内容）一起变透明
属性名：opacity
属性值：0~1之间的数字
	1：表示完全不透明
	0：表示完全透明
注意点：
opacity会让元素整体透明，包括里面的內容，如：文字、子元素等…（哈哈我之前做[[#学成在线]]那个项目就被这个坑过，[[#PxCook]]给我opacity，我还纳闷为什么字也变透明了，后来背景色换了rbg就好了）

纯写css一般不会用，一般用来配合js做效果


%%直接跳了三个拓展
选择器拓展可以看看 pink 老师 100 来集左右那两个视频%%

## 项目样式补充
目标：能够 使用精灵图，能够给元素 添加阴影效果，能够让元素完成 过渡效果


### 精灵图
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220824000915.png)

场景：项目中将多张小图片，合并成一张大图片，这张大图片称之为精灵图；之后的单个logo实际上是截取大图的一部分
优点：减少服务器发送次数，减轻服务器的压力，提高页面加载速度

#### 精灵图的使用步骤
1. 创建一个盒子，设置盒子的尺寸和小图尺寸相同
	1. 精灵图的标签都用行内标签 span, b, i（行内标签转换为行内块，否则无法撑开）
	2. 在pxccok里量出小logo的精准像素
2. 将精灵图设置为盒子的[[#背景图片]]
3. 修改背景图位置
	通过 PxCook 测量小图片左上角坐标，分别取**负值**设置给盒子的 background-position: x  x（水平先 垂直后 往左往上给负数）[[#背景位置]] ^ico3n6

### 文字阴影
没有课
弹幕：文字阴影是做火焰字或者 3D 字的，这方面 CSS 真不如 PS，还不实用


### 盒子阴影
[Box Shadow CSS Generator | CSSmatic](https://www.cssmatic.com/box-shadow)

作用：给盒子添加阴影效果，吸引用户注意，体现页面的制作细节
属性名：`box-shadow`
取值：（都用空格隔开）
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825144518.png)

%%不用自己设计，设计师会设计好的hhh%%

最后一个词只能写inset，外阴影是默认，不要写outset

### 过渡
作用：让元素的样式慢慢的变化，常配合 hover 使用，增强网页交互体验%%苹果动效🤔%%
属性名：transition
常见取值：
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825192427.png)

注意点：
1. 过渡需要：默认状态 和 hover状态样式不同，才能有过渡效果
2. transition属性给需要过渡的元素本身加（而不是hover加）
3. transition属性设置在不同状态中，效果不同的
	给默认状态设置，鼠标移入移出都有过渡效果
	给 hover 状态设置，鼠标移入有过渡效果，移出没有过渡效果

`transition: width 1s, background-color 2s` 单个变，写具体属性，用逗号隔开
`transition: all 1s` 全部变，如果变化的属性多，直接写all，表示所有




# 项目

## 学成在线

### 根目录

项目的根目录文件夹一般用英文命名（要上传到[[vps|服务器]]），下存所有素材（文件、图片），也要用英文

1. 图片文件夹：images
2. 样式文件夹：CSS 
	配套的 css 样式文件和 html 同名
	引入![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220821182618.png)

3. 首页：index. html
	所有网站的首页都叫index，因为服务器找首页都是找index.html

[[VS Code]] 分屏

布局思路：从外到内，从上到下，从左到右

![[#css 书写顺序]]

### 清除默认样式
一律不会自己写，直接复制统一的
```css
* {
    margin: 0;
    padding: 0;
    /* 内减模式：m、p不会撑大盒子 */
    box-sizing: border-box;

}

/* 清除li圆点 */
li {
    list-style: none;
}

/* 清除标签下划线 */
a {
    text-decoration: none;
}

/* 清除浮动 */
.clearfix:before,
.clearfix:after {
    content: "";
    display: table;
}

.clearfix:after {
    clear: both;
}

```


### 版心居中

版心居中：版心命名「wrapper」

`<div class="header wrapper"> </div>`  
标签可以同时调用两个类名，header 和 wrapper
	wrapper 添加版心居中效果
	header 负责头部样式

版心只有这两个效果，居中和宽度
```css
.wrapper {
    margin: 0 auto;

    width: 1200px;
}
```



### header 布局

高度直接取 logo 的高度，logo 是文件里的图片格式，直接看属性

先给背景色 好定位和感知大小，写完就取消掉

#### logo
logo : h1>a>img
	最重要的>跳转回首页>logo图片

⚠️ 初学者最好写完一个标签折叠一下（左侧三角），防止写错位置

#### nav 布局
纯文字区域可以不给宽（还是要给高的），因为文字非常稳定，可以撑开

只要导航，必须是ul>li>a

导航下的边（悬停出现）通过给a加padding和border实现

```html
        <!-- 导航 -->
        <div class="nav">
            <ul>
                <li><a href="">首页</a></li>
                <li><a href="">课程</a></li>
                <li><a href="">职业规划</a></li>
            </ul>
        </div>
```

```css
/* 导航 */
.nav {
    float: left;

    height: 42px;

    margin-left: 70px;
}

.nav li {
    /*防止污染其他li*/
    float: left;

    padding: 0 9px;
    margin-right: 26px;
}

.nav li a {
    display: block;

    height: 42px;
    line-height: 42px;

    padding: 0 9px;

    font-family: MicrosoftYaHei;
    font-size: 18px;
    color: #050505;
}

.nav li a:hover {

    border-bottom: 2px solid #00a4ff;

}
```



#### 搜索 布局、文本框、按钮
搜索键其实是一张图片，直接看图片宽高大小就好
笑死，做网页布局要疯狂做加减乘除数学

控制 placeholder 的样式（搜索框内文字）
`.search input::placeholder `
不这样写的话会影响输入的文字样式

图片有两种
	[[HTML#图片标签（img）]]和[[CSS#背景图片]]
	按钮首选background（对于美化、装饰的图，都采用背景） ^c88q8b


#### 用户区域

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220823002000.png)
给高不给宽，因为用户名长度不确定

头像用img

### banner (轮播图)

通栏盒子（宽度和浏览器宽度一样）

#### 左边
不用上padding 用行高（选中字就会出现行高数据）

### 版权
要放到最底下
清除浮动不是直接清除自身，而是清除上面导致无法撑开的浮动，clearfix 写在标签的 class 里

发现我总是喜欢用div而不是p，要注意一下




# 小兔鲜
## 项目前置认知

目标：能够知道 SEO三大标签，能够设置网页的 icon图标，能够书写版心公共类代码

### 骨架结构标签

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825193654.png)

#### DOCTYPE文档说明
`<!DOCTYPE html＞` 文档类型声明，==告诉浏览器==该网页的 HTML版本
`<!DOCTYPE html＞` 就是时下最流行的html5

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825193542.png)

#### 网页语言
`<html lang="en"＞`标识 网页 使用的 语言
作用：搜索引擎归类 +浏览器翻译
常见语言：zh-CN 简体中文 / en 英文

不改也不影响显示，当是英文的时候，谷歌会提示是否翻译的

#### 字符编码（了解）
`<meta charset="UTF-8">` 标识 网页 使用的字符编码

作用：保存和打开的字符编码需要统一设置，否则可能会出现 乱码

常见字符编码：
	1. UTF-8：万国码，国际化的字符编码，收录了全球语言的文字
	2. GB2312：6000+ 汉字
	3. GBK： 20000+ 汉字

注意点：开发中统一使用 UTF-8 字符编码即可

#### 其他
`<meta http-equiv="X-UA-Compat ible" content="IE=edge">` IE 浏览器兼容性

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`
宽度=设备宽度，做移动端的时候要用


### SEO 三大标签

#### SEO简介
SEO (Search Engine Optimization) 搜索引擎优化
作用：让网站在搜索引擎上的排名靠前

提升SEO的常见方法：
1. 竞价排名
2. 将网页制作成html后缀
3. 标签语义化（在合适的地方使用合适的标签）[[HTML#标签语义化]]

#### SEO三大标签
1. title：网页标题标签
2. description：网页描述标签
3. keywords：网页关键词标签
（后两个用meta标签写）

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825204418.png)

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825205205.png)

### ico 图标设置（浏览器标题栏图标）
favicon

场景：显示在标签页标题左侧的小图标，习惯使用. ico 格式的图标，直接放在根目录
常见代码：
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825205421.png)

## 项目结构搭建

目标：能够使用专业方式完成 项目结构搭建 和基础公共样式

学习路径：
- [[#文件和目录准备|文件和目录准备]]
- [[#基础公共样式|基础公共样式]]
- [[#index页面骨架|index页面骨架]]


### 文件和目录准备
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825205737.png)
uploads 是用户上传的图

base：清除默认样式的代码

![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220825210629.png)
引入 css 的时候要按照 base、common、index 的顺序引入
外链式的时候，谁在下（后写的）谁生效


### 基础公共样式
直接复制进去  [base.css](file:///Users/gnblink/Downloads/base.css)

版心写在common里

快捷菜单（快捷导航）shortcuts：最上面的导航



# 其他

- [[Vs Code]]简便写法
	- h100+w100+bgc 

[The ultimate CSS tools for web designers | CSSmatic](https://www.cssmatic.com/)
[色彩选择工具 - CSS（层叠样式表） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Colors/Color_picker_tool)
[CSS 按钮生成器](https://css3buttongenerator.com/)


## 颜色的常见取值
如：文字颜色：color
如：背景颜色：background-color

属性值：
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220622110129.png)

rgba
a的取值范围：0~1
	1：完全不透明
	0：完全透明
省略写法：rgba(0,0,0,0.5）可以省略写成 rgba (0, 0, 0,.5)

原理和rgba一样，但是用16进制表示
![](https://cdn.jsdelivr.net/gh/Gnblink0/Picture/img/20220622110528.png)
实际开发中会直接使用测量工具直接得到颜色，不需要前端自己设计颜色，直接复制粘贴即可。

综合案例1-新闻网页案例
综合案例 2-卡片居中案例



## PxCook
目标：能够使用 PxCook 工具测量设计图的 尺寸和颜色，能够从psd文件中直接获取数据
学习路径：
1. 打开设计图
2. 常用快捷键
3. 从 psd 文件中直接获取数据

### PxCook的基本使用
1. 通过软件打开设计图
① 打开软件② 拖拽入设计图 ③ 新建项目

2. 常用快捷键
放大设计图：`ctrl +`
缩小设计图：`ctrl -`
移动设计图：空格按住不放，鼠标拖动

3. 常用工具
量尺寸
吸颜色

4. 从psd文件中直接获取数据
切换到开发界面，直接点击获取数据




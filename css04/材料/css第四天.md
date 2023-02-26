## 一、css3新增的选择器

### 属性选择器（了解）

根据元素的属性及属性值来选择元素；

**语法：元素名称[相关属性] { css样式 }**

#### 属性名称选择元素

语法：**标签选择器[属性] {}**，通过某一个属性选择元素

```css
        /* 表示选中了input标签，而且标签有一个type属性 */
        input[type] {
            background-color: blueviolet;
        }
```

#### 属性值选择元素

语法：**标签选择器[属性=属性值] {}**，通过某一个属性和属性值选择元素；

```css
        /* 表示选中了input标签，而且标签有一个type属性,属性的取值为url */
        input[type=url] {
            background-color: green;
        }
```

注意：属性值的引号可以省略不写；

#### 属性值以某一个字符开头

语法：**标签选择器[属性^=属性值里面的字符]**，

通过某一个属性选择元素，但是属性值必须是以某一个字符开头的

```css
        /* 表示选中了input标签，而且标签有一个type属性,属性的取值必须是以t字符开头的 */
        input[type^=t] {
            background-color: gold;
        }
```

**注意：** ^= 后面的值不能是纯数字或者以数字开头，必须是字母

#### 属性值以某一个字符结尾

语法：**标签选择器[属性$=属性值里面的字符]**，

通过某一个属性选择元素，但是属性值必须是以某一个字符结尾的

```css
        /* 表示选中了input标签，而且标签有一个type属性,属性的取值必须是以h字符结尾的 */
        input[type$=h] {
            background-color: orangered;
        }
```

**注意：** $= 后面的值不能是纯数字或者以数字开头，必须是字母

#### 属性值包含某一个字符

语法：**标签选择器[属性*=属性值里面的字符]**，通过某一个属性选择元素，但是属性值不管在什么位置只要包含某一个字符即可选中；

```css
        /* 表示选中了input标签，而且标签有一个type属性,属性的取值不管什么位置只要包含r就会被选中 */
        input[type*=r] {
            background-color: rgb(255, 0, 106);
        }
```

**注意：** *= 后面的值不能是纯数字或者以数字开头，必须是字母

### 结构伪类选择器（死了都要会）

css3结构伪类选择器根据html的结构顺序来选择元素，比如选择第一个，最后一个，某一个等；

#### :nth-child 选择器（重点）

通过nth-child选择元素是将这个父级盒子中的所有子元素依次排序，然后按照对应的顺序选择元素，不会将元素分类（比如男生女生混合的排序）

**查找方法：先查看位置，然后再去匹配是不是对应的标签，如果选择的位置，元素不匹配则不会渲染样式；**

##### 第一个元素:first-child {}

选择结构中指定的第一个元素；

```css
        /* 表示选中了box盒子里面所有的li中的第一个 */
        .box li:first-child {
            background-color: palegreen;
        }
```

##### 最后一个元素:last-child {}

选择结构中指定的最后一个元素；

```css
        /* 表示选中了box盒子里面所有的li中的最后一个 */
        .box li:last-child {
            background-color: palegreen;
        }
```

##### 倒数第几个:nth-last-child(n)

选择结构中指定的倒数第n个元素；

```css
        /* 表示选中了box盒子里面所有的li中的倒数第3个元素 */
        .box li:nth-last-child(3) {
            background-color: pink;
        }
```

##### 某一个元素:nth-child(n)

选择结构中指定的第n个元素；

```css
        /* 表示选中了box盒子里面所有的li中的指定的位置的元素 */
        .box li:nth-child(3) {
            background-color: powderblue;
        }
```

#### 伪类选择器n的取值(重点)

##### 01、**直接取值为n**

  表示选中所有的该标签

##### 02、取值为关键字odd或者even

**odd 表示取值为奇数**

```css
	 .box li:nth-child(odd) {
            background-color: pink;
      }
```

**even 表示取值为偶数**

```css
	.box li:nth-child(even) {
            background-color: palegreen;
     }
```

##### 03、取值为数学公式

​	2n表示偶数；
​	2n+1 表示奇数；
​	3n表示取值为3的倍数；
​	n+3表示从第3个开始一直选择到最后一个；
​	-n+3表示表示前3个；

### :nth-of-type选择器（了解）

**选择元素的规则：**先将父级里面元素分类（比如班级里的学生分为男生和女生）并且各自排序，然后再去匹配位置；

#### 第一个元素:first-of-type 

选择父元素下某一类元素的第一个元素

```css
	.box div:first-of-type {
            background-color: gold;
        }
```

#### 最后一个元素:last-of-type 

选择父元素下某一类元素的最后一个元素

```css
	 .box div:last-of-type {
            background-color: gold;
        }
```

#### 某一个元素:nth-of-type(n)

选择器父元素下某一类标签中的第n个元素

```css
        .box p:nth-of-type(2) {
            background-color: palegreen;
        }
```

**注意：:nth-of-type(n) 中 n的取值个nth-child是一样的**；

## 二、伪元素

### 概念理解

伪元素可以帮助我们**利用CSS创建新html标签元素**，而**不需要在HTML结构中书写**该html标签，从而**简化HTML结构**；

新创建的这个元素在html结构中是找不到的，所以我们称为伪元素；它不是真正意义上的元素；

### 伪元素的分类

#### ::before  

在元素内容前面插入一个伪盒子

```css
    .box::before {
        content: '';
    }
```

#### ::after 

在元素内容后面插入一个伪盒子

```css
    .box::after {
        content: '';
    }
```

### 伪元素注意事项和特点

01、**伪元素必须添加给双标签**，如果加给单标签是不生效的；

02、**伪元素设置的时候必须添加content属性**，否则不生效，哪怕是空的也要设置空的引号；

03、**伪元素的显示模式默认是行内元素的特点**，直接设置宽高是无效的，我们需要转化；

04、伪元素的权重值为1；



## 三、传统网页布局 --- 浮动布局

实际开发中传统的网页布局主要是3块技术完成的，包括**标准流布局，浮动布局，定位布局**；

### 标准流布局（文档流布局）

浏览器在渲染显示网页内容时采用的一套排版规则，规定了应该以何种方式排列元素；

**块元素：**从上往下，垂直布局，独占一行；

**行内元素/行内块元素：**从左往右，水平布局，空间不够会自动折行；

### 浮动布局

#### 为什么需要浮动？

有很多的布局效果，标准流没有办法完成，此时就可以利用浮动完成布局。

#### 浮动最初的作用 --- 文字环绕效果

浮动最初的时候是为了实现文字环绕元素的效果；

![](assets/01.png)

#### 浮动的基本语法

语法：**float:浮动模式；**

浮动float的取值也就是浮动模式取值有**left、right**、none；

**左浮动 fll** 

```css
 float: left;
```

**右浮动 flr**

```css
float: right;
```

**不浮动**

```css
 float: none;
```

#### 浮动的特点

##### 脱标

01、浮动的元素脱离标准流，在标准流中不占据位置；
02、浮动元素脱标以后，只能影响后面盒子的布局，不会影响前面盒子的布局；

##### 浮动的元素具有行内块元素的特点

01、元素一行多个显示，但是没有缝隙，并且顶端对齐；
02、如果不设置固定的宽，默认的宽度是内容撑开的；
03、可以设置宽高和内外边距都生效；

#### 使用浮动布局需要注意事项（死了都要记）

01、浮动布局的时候一定要配合一个标准流的父级盒子来限制浮动元素的位置；
02、如果父元素中的子元素布局的时候，一个浮动了其他的子元素也要浮动，否则会出现问题；

03、如果父元素里面的子元素浮动以后，所有的宽度包括margin值加起来大于父盒子的宽度，子盒子会折行另起一行显示；

**解决方案1**：使用css3的结构伪类选择器，选中每一行的最后一个设置某一个数的倍数，设置外边距为0即可；

```css
.list-box .pr li:nth-child(4n) {
  margin-right: 0;
}
```

以上的代码表示选中了4的倍数的盒子设置margin-right为0；

**解决方案2：**列表的父级盒子默认和最外层的大盒子一样大，我们可以设置列表的父级盒子比外层的大盒子宽103%，这样就可以兼容任何浏览器；

```css
.list-box ul {
  /* width: 992px; */
  width: 103%;
  /* height: 600px; */
  /* background-color: rgba(0, 0, 0, 0.6); */
}
```

### 清除浮动

#### 清除浮动的原因

有些情况下**父级盒子不能给固定的高度**(比如文章详情页，无限加载的列表页)，父级盒子的高度是内容撑开的,**如果子级盒子浮动了，子级盒子就会脱离文档流，导致父级盒子高度不被撑开为0的问题**，就会影响下面盒子的显示;

![](assets/01.jpg)

#### 清除浮动属性clear

清除左浮动：clear:left;
清除右浮动：clear:right;
**清除两者（常用）：clear: both;**  

#### 清除浮动的方案

##### 01、额外标签法

W3C推荐使用，但是我们不推荐使用，因为多出了很多无用的空标签；
**找到父级盒子中浮动的最后一个元素，紧跟着书写一个块级盒子设置清除浮动的属性即可**

![](assets/02.jpg)

##### 02、父级开启BFC法（BFC）

​       直接在父级盒子的css中添加overflow: hidden;即可开启父级盒子BFC布局模式；

##### 03、使用after伪元素法（重要）

伪元素是通过css给页面添加结构标签，但是在html结构中看不到该标签；

```css
        /*声明清除浮动的样式*/
        .clearfix:after {
            content: "";
            display: block;
            height: 0;
            visibility: hidden;
            clear: both;
        }

        .clearfix {
            *zoom: 1;
            /*ie6,7 专门清除浮动的样式*/
        }
```

> ```
> 01、after表示在clearfix的双标签盒子的内容后面添加了一个伪元素盒子；
> 02、content属性是伪元素必须要书写的属性，哪怕空着也有，空的就书写一个空的英文引号即可；
> 03、伪元素默认的显示默认是为行内元素，所以要转化为块dispaly：block；
> 04、visibility: hidden;占位隐藏；
> 05、clear: both;清除浮动的影响；
> ```

**使用方法**：**谁的子级盒子浮动了，就用调用clearfix类名；**

![](assets/03.jpg)

##### 04、使用双伪元素清除浮动

```css
        /*声明清除浮动的样式*/
        .clearfix:before,
        .clearfix:after {
            content: "";
            /* 让伪元素在一行显示 */
            display: table;
        }

        .clearfix:after {
            clear: both;
        }

        .clearfix {
            *zoom: 1;
            /*ie6,7 专门清除浮动的样式*/
        }
```

**使用方法：谁的子级盒子浮动了，就用调用clearfix类名；**

![](assets/04.jpg)

## 四、导航的书写思路（重要）

### html结构

```html
    <div class="nav">
        <ul>
            <li><a href="#">首页</a></li>
            <li><a href="#">体检医院</a></li>
            <li><a href="#">体检套餐</a></li>
            <li><a href="#">个人中心</a></li>
        </ul>
    </div>
```

nav盒子代表导航的整体，ul嵌套li代表导航的列表，a需要实现跳转功能；

### css样式

```css
        /* 第一步：设置nav的相关实体化样式 （宽高背景）*/
        .nav {
            width: 1200px;
            height: 45px;
            margin: 0 auto;
            background-color: #6BA827;
        }

        /* 第二步：让li在一行显示 */
        .nav li {
            float: left;
        }

        /* 第三步：设置li里面a的样式 */
        .nav li a {
            /* 01、a是行内元素不能直接设置宽高，需要转化为块 */
            display: block;
            height: 45px;
            /* 02、宽度不需要设置，因为文字的个数不一样，我们用padding:0 你的值; */
            padding: 0 20px;
            /* background-color: coral; */
            font-size: 18px;
            color: #fff;
            line-height: 45px;
        }

        /* 第四步：设置鼠标经过a的样式 */
        .nav li a:hover {
            background-color: darkgreen;
        }
```



## 五、css书写顺序（了解）

建议遵循以下顺序：

1. **布局定位属性**：display / position / float / clear / visibility / overflow（建议 display 第一个写，毕竟关系到模式）
2. **自身属性**：width / height / margin / padding / border / background
3. **文本属性**：color / font / text-decoration / text-align / vertical-align / white- space / break-word
4. **其他属性（CSS3）**：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient …

```css
 .jdc {
    display: block;
    position: relative;
    float: left;
    width: 100px;
    height: 100px;
    margin: 0 10px;
    padding: 20px 0;
    font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
    color: #333;
    background: rgba(0,0,0,.5);
    border-radius: 10px;
 }
```

## 六、css的BFC（面试必备）

### 定义

**块格式化上下文（Block Formatting Context，BFC）**

**通俗理解**：**BFC是一个独立的布局环境，BFC里面的子元素不会影响外界的元素**，所以我们可以**用BFC来解决外边距塌陷，外边距合并、清除浮动等问题**；

### 触发 BFC

只要元素满足下面任一条件即可触发 BFC 特性：

> - html，body 根元素；
> - 浮动元素：float 除 none 以外的值；
> - 绝对定位元素：position (absolute、fixed)；
> - display 为 inline-block、table-cells、flex，flow-root，除了block其他基本都是可以触发BFC的；
> - overflow 除了 visible 以外的值 (hidden、auto、scroll)

**我们最常用的是**：overflow:hidden;  display:flow-root;

###  display:flow-root

给元素设置display:flow-root，元素就会变成块级元素，同时这个元素会建立新的块级格式上下文（也就是触发了BFC模式）；

### 查看属性技术的兼容性

https://caniuse.com/?search=display%3Aflow-root

## 案例

01、导航的写法

![](assets/04.png)

02、学成在线列表

![](assets/03.png)

03、小米手机

![](assets/02.png)

## 作业

学成在线网站书写


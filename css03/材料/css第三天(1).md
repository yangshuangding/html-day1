## 一、css三大特性

### 01、层叠性（覆盖性）

一个标签的同一个属性被多次重复设置，最后设置的一次会生效，其他的都会被层叠覆盖；

遵循了**就近原则**；

```css
    .box {
        width: 300px;
        height: 300px;
        background-color: royalblue;
        width: 100px;
    }
```

以上代码盒子的宽度最终大小为100px，将最前面的300px覆盖掉了；

### 02、继承性

有一些css属性子级元素可以继承父级元素的样式，不需要单独设置，控制文字的相关属性（text-，font-，line-，color）几乎都可以被继承；

**注意：**01、超链接a元素不会继承父级盒子的color颜色，因为浏览器默认给a设置默认的颜色样式，我们需要单独设置a的color颜色；

![](assets/01.png)

02、标题标签除了h4以外所有的h标签不会直接继承父级盒子的文字大小font-size，因为他们本身自己有默认的文字大小并且是em相对单位，我们得到的**结果是我们设置父级文字大小乘以这个倍数**；所以我们需要单独设置；

虽说h4可以继承父级的文字大小，但是我们还是建议单独设置；

![](assets/02.png)

### 03、权重优先级

不同的选择器选择元素的时候权重大小不同，我们以基础选择器为参照，计算出我们自己选择器权重大小；

#### 基本计算

01、继承性和通配符选择器是没有权重的，如果当前元素自己有样式，就不会继承父级的样式，所以**继承性和通配符选择器的权重为0**；

02、标签选择器，伪元素的权重为1 （0,0,0,1）

03、类选择器，伪类选择器，属性选择器的权重为10    （0,0,1,0）

04、id选择器的权重为100    （0,1,0,0）

05、行内样式的权重为1000   （1,0,0,0）

06、可以给样式设置!important  提高权重 ，权重是无限大，**继承性的权重是无法被提升的**；

#### 权重叠加

实际开发中我们往往是按照复合选择器书写样式，所以我们就会将一些权重进行叠加计算,比如以下代码就可以计算出不同的权重值；

```CSS
     .box li a {
         color: red;
     }
     .box li a:hover {
        color: salmon;
     }
```

 .box li a  的权重值 = 0,0,1,0 + 0,0,0,1 + 0,0,0,1 = 0,0,1,2 = 12

.box li a:hover的权重值 =  0,0,1,0 + 0,0,0,1 + 0,0,0,1 + 0,0,1,0 = 0,0,2,2 = 22

**注意**:**权重叠加是不会有进位的**，每一类基础选择器只能在自己的位置叠加，如果超过10也不能向前进位哦；相当于现实辈分和年龄是不能对比的；

#### 课堂练习

6道精华题

## 二、盒子模型（重点）

### 网页布局本质

所谓的网页布局就是利用 CSS 摆放盒子，我们需要设置盒子的占位大小，设置盒子不同的摆放位置；

### 盒子模型的基本组成部分

一个完整的布局盒子主要包括内容content，边框border，外边距margin，内边距padding；

#### 内容content

我们自己设置的宽高或者盒子默认的宽高；

#### 边框border

##### 边框三要素

盒子的边框设置，border是有三个要素组成的：**边框样式border-style，边框粗细border-width，边框颜色border-color**

```css
    border-style: solid;
    border-width: 2px;
    border-color: red;
```

**注意**：边框样式border-style取值常见的有**实线solid，虚线dashed，点线dotted，双线double**，默认取值为none；

##### border的综合写法

**语法：*border*: 线条样式   线条粗细  线条颜色;**

```css
    /* 
	border-style: solid;
    border-width: 2px;
    border-color: red; 
	*/
    border: solid 2px red;
```

##### 设置不同方向的边框

**语法：border-方位名词：线条样式   线条粗细  线条颜色；**

```css
    border-top: solid 2px red;
    border-bottom: solid 2px red;
    border-left: solid 2px red;
    border-right: solid 2px red;
```

##### 设置单独某个方向的某个属性

**语法：border-方位名词-属性：属性值；**

```css
    border-left-color: red;
    border-right-style: solid;
    border-top-width: 3px;
```

#### 外边距margin

**作用：**设置两个盒子之间的距离；

![](assets/04.png)

##### 设置不同方向的内边距

**语法：margin-方位名词：值；**

```css
    margin-left: 20px;
    margin-right: 20px;
    margin-top: 20px;
    margin-bottom: 20px;
```

##### 取值个数不同

取值为1个值表示四个方向都一致；

```css
margin: 20px;
```

取值为2个值表示： **上下   左右**；

```css
margin: 20px  30px;
```

取值为3个值：**上   左右  下**；

```
margin: 20px  10px  5px;
```

取值为4个值：**上  右   下  左；**

```
margin: 20px  30px  8px 80px;
```

#### 内边距padding

**作用：**设置内容距离盒子边缘的距离；

![](assets/03.png)

##### 设置不同方向的内边距

**语法：padding-方位名词**

```css
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 20px;
    padding-bottom: 20px;
```

##### 取值个数不同

取值为1个值表示四个方向都一致；

```css
padding: 20px;
```

取值为2个值表示： **上下   左右**；

```css
padding: 20px  30px;
```

取值为3个值：**上   左右  下**；

```
padding: 20px  10px  5px;
```

取值为4个值：**上  右   下  左；**

```
padding: 20px  30px  8px 80px;
```

## 三、盒子模型相关布局问题以及技巧（重点）

### 01、盒子的实际大小计算

盒子的实际占位大小指的就是我们**设置好宽高的基础上累加padding和border的大小**；

**盒子的实际宽度  = 内容width + 左右的padding + 左右的border；**

**盒子的实际高度  = 内容height+ 上下的padding + 上下的border；**

![](assets/05.png)

### 02、padding和border撑大盒子问题

如果盒子宽高设置固定了，再去给盒子添加padding和border就会将盒子的大小撑大；

#### **解决方案1：人为手动加多少减多少**：

加多少减多少，将我们自己设置的宽高减去对应的padding和border即可；

![](assets/07.png)

#### 解决方案2：开启css3的盒子内减模式

直接给盒子设置css3的内减模式 **box-sizing: border-box;**

浏览器在解析的时候就会自己算我们的尺寸，会将设置的padding和border全部减去然后重新计算盒子的大小；

![](assets/06.png)

### 03、外边距塌陷问题（了解）

#### 情况1：上下排列的盒子外边距合并

**上下排列的两个盒子，上面的盒子设置了margin-bottom,下面的盒子设置了margin-top，最终显示的样式两个值谁大就显示谁，小的值被大的值合并了；**

解决方案1：单独设置给其中某一个盒子，不要两者都设置；

解决方案2（不推荐使用）：将两个小盒子单独嵌套在一个父级盒子中，然后给父级开启BFC模式

#### 情况2：嵌套盒子外边塌陷（外边距穿透）

如果两个盒子有嵌套包含的父子级关系，如果给子级盒子设置了margin-top，外边距就会穿透了父级盒子显示，效果显示父级盒子也会跟着掉下来；

![](assets/04.jpg)

**解决方案1：**给父级盒子设置边框border，必须要设置border-top，如果父盒子本身就有border就不会出现塌陷问题；

**解决方案2：**给父级盒子设置内边距padding，必须要 设置padding-top，如果父盒子本身就有padding就不会出现塌陷问题；

**解决方案3：**给父级盒子设置overflow:hidden；、display:flow-root；利用盒子的BFC模式；



### 04、外边距的经典应用：设置盒子水平居中

想要使用**margin:0 auto;**设置一个盒子居中必须满足两个条件： 

> 01、盒子必须是独自占一行的块元素；
>
> 02、盒子必须要有固定的宽度；
>

**注意：实际开发中最常用就是设置版心盒子居中；**

**版心：**网页主体内容的显示区域，一般是一个固定宽度的盒子，在浏览器的中心显示；版心的类名一般用w或者container表示；目前市场的版心一般都在1200左右（传智1200，京东1190、小米1226）；

![](img/jd.png)

**实际的开发中版心是不需要固定高度的，因为每一个模块的高度不一样；**

```css
        .w {
            width: 1200px;
            margin: 0 auto;
        }
```

![](assets/08.png)

### 004、行内元素和行内块元素居中text-align：center；

将行内元素和行内块元素放在一个父级盒子中，设置父级盒子tac即text-align：center；就可以居中

### 05、清除内外边距

有些html标签浏览器在解析的时候有默认的内边距padding或者外边居marign，我们需要将默认的样式清除，再去设置自己的样式；

比如：body有8px的默认外边距，ul有默认的内边距等

我们只需在css的最前面将所有标签的margin和padding清0即可；

```css
    * {
        margin: 0;
        padding: 0;
    }
```

### 06、细线表格（边框合并）--- 死了都要记

实际工作我们经常使用表格展示数据，我们用css设置细线表格，我们只需要给table、th、td标签同时设置边框border，然后设置边框合并属性*border-collapse*: collapse;即可实现；

```css
        table,
        th,
        td {
            border: 1px solid #ccc;
            border-collapse: collapse;
        }
```

![](assets/20.png)

### 07、border书写三角形效果（了解）

![](assets/21.png)

盒子宽高必须都是0，然后设置盒子四条边都是透明，最后单独设置一个方向的边的颜色即可；

```css
    width: 0;
    height: 0;
    border: 20px solid transparent;
    border-top-color: red;
```

## 四、css的BFC（面试必备）

### 定义

**块格式化上下文（Block Formatting Context，BFC）**

**通俗理解**：**BFC是一个独立的布局环境，BFC里面的子元素不会影响外界的元素**，所以我们可以**用BFC来解决外边距塌陷，外边距合并、清除浮动等问题**；

### 触发 BFC

只要元素满足下面任一条件即可触发 BFC 特性：

> - html，body 根元素；
> - 浮动元素：float 除 none 以外的值；
> - 绝对定位元素：position (absolute、fixed)；
> - display 为 inline-block、table-cells、**flex，flow-root**，除了block其他基本都是可以触发BFC的；
> - overflow 除了 visible 以外的值 (hidden、auto、scroll)

**我们最常用的是**：overflow:hidden;  display:flow-root;

### display:flow-root

给元素设置display:flow-root，元素就会变成块级元素，同时这个元素会建立新的块级格式上下文（也就是触发了BFC模式）；

### 查看属性技术的兼容性

https://caniuse.com/?search=display%3Aflow-root



## 案例

01、  

![](assets/09.png)

2、                

![](assets/10.png)

## 作业

01、我的课程

![](assets/11.png)

02、小米登录

![](assets/12.png)

03、爱宠知识（选做）

![](assets/13.png)
















































































































































































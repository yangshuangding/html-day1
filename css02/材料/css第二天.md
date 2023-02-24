##  一、复合选择器简介

**由两个或多个基础选择器，通过不同的方式组合而成的，可以更准确、更高效的选择目标元素（标签）；**

**就比如生活中找一个人：找杭州黑马程序员的老王**

第一种方式：直接找老王，相当于我们的基础选择器，如果不止一个老王就会全部选中；

第二种方式：通过对应的路径找目标老王，比如：杭州   黑马程序员 前端学科的老王，这样就会更加准确的选择目标元素，相当于我们的复合选择器；

复合选择器我们主要学习后代选择器、子代选择器、交集选择器、并选择器

## 二、复合选择器分类

### 后代选择器（死了都要用）

html结构存在嵌套的父子级或者后代关系（比如：ul无序列表）

**基本语法**

 **选择器1    选择器2 {  css样式 }**

01、选择器1相当于父级元素，选择器2相当于后代元素，之间**用空格隔开表示后代关系**；

02、后代元素可以是子元素，也可以是孙子级别的元素，只要有嵌套关系就可以查找到；

```html
 
   ul li {
       color: red;
   }

   .box .son {
       color: green;
   }
  </style>

  <ul>
    <li>我是无序列表</li>
    <li>我是无序列表</li>
    <li>我是无序列表</li>
 </ul>
<div class="box">
    <div class="son"></div>
 </div>
```

**案例：**书写导航的基本结构，设置超链接a的颜色为#333和文字大小为18px；

```html
.nav>ul>li*3>a + 回车
<div class="nav">
    <ul>
        <li><a href="#">首页</a></li>
        <li><a href="#">产品分类</a></li>
        <li><a href="#">联系我们</a></li>
    </ul>
</div>
```



### 子代选择器（亲儿子选择器）

html结构必须是父子级的嵌套关系，只能选择第一级的嵌套，不会选择里面的孙子；

**基本语法**

 **选择器1>选择器2 {  css样式 }**

01、选择器1相当于父级元素，选择器2相当于子元素，之间**用大于号>连接表示选中第一级的子元素**；

02、后代元素必须是子元素（亲儿子），不可以是孙子级别的元素；

```html
    <style>
        .box>p {
            color: red;
        }
    </style>
    <div class="box">
        <p>我是亲儿子级别的p标签1</p>
        <p>我是亲儿子级别的p标签2</p>
        <p>我是亲儿子级别的p标签3</p>
        <div class="son">
            <p>我是孙子级别的p标签1</p>
            <p>我是孙子级别的p标签2</p>
            <p>我是孙子级别的p标签3</p>
        </div>
    </div>
```

**注意：子元素选择器只能选择嵌套的父子级的子级盒子，可以理解为亲儿子选择器**

### 交集选择器

选中页面中 同时满足 多个选择器的标签，满足**即又的关系**，**主要是可以提高被选择元素的权重**；

**基本语法**

 **选择器1选择器2 {  css样式 }**

01、交集选择器可以更加精准的选择某一个元素，**相当于即又关系**，也就是两个需求都要满足（比如：我要找一个人，这个人是男生并且有个名字叫老王  ----  男生老王）；

02、最常用的还是**标签选择器和类选择器的搭配使用**,选择器2也可以是id选择器；

03、交集选择器两个选择器之间是绝对不能书写空格，有了空格就会变成后代选择器；

```html
    <style>
        .box {
            font-size: 30px;
            color: red;
            font-weight: 700;
        }
        /* 要求：让命名为box的p标签颜色为老王绿 */
        /* 选择器1选择器2 {  css样式 } */
        p.box {
            color: lawngreen;
        }
    </style>
      <div class="box">我是div</div>
    <p class="box">我是p标签</p>
    <span class="box">我是span</span>
```

**注意：交集选择器后期经常用来提升元素的选择权重**；



### 并集选择器

**同时选择多组标签，设置相同的样式**；

如果一些元素样式完全一致，我们可以通过并集选择器合并起来书写，达到代码简化的作用；

**基本语法**

 **选择器1，选择器2,...... {  css样式 }**

并集选择器我们经常用来**集体声明某一些标签的共有样式**，比如我们经常在css的前面设置i和em标签的倾斜样式为不倾斜方便咱们在页面中使用；

```html
    <style>
        i,
        em {
            font-style: normal;
        }
    </style>
```



### 伪类选择器

#### 基本介绍

所有的html标签都可以设置伪类，我们只需要用英文状态的**冒号( : )将选择器和伪类状态连接**即可；

**基本语法**

 **选择器:伪类状态 {  css样式 }**

**常见的伪类状态有：** :link，:visited ，:hover，:active 四种状态，还有一种特殊专门作用于表单元素获取焦点状态的 :focus伪类选择器。

#### 常见伪类状态（了解）

选择器:link         鼠标未访问的链接（访问前）
选择器:visited    鼠标已访问的链接（访问后）
选择器:hover      鼠标移动到链接上（鼠标经过）
选择器:active      鼠标选定的链接（按下鼠标的时候）

**注意：**如果以上四个状态都要书写必须按照L~V~H~A的顺序来书写，否则就会失去效果；

```html
    <style>
        /* 鼠标访问前 */
        a:link {
            color: red;
        }

        /* 鼠标访问后 */
        a:visited {
            color: green;
        }

        /* 鼠标访问的时候 */
        a:hover {
            color: royalblue;
        }

        /* 鼠标按下的时候 */
        a:active {
            color: tomato;
        }
    </style>

    <a href="#"></a>
```

#### 伪类选择器实际工作的用法（死了都要记）

实际开发中我们不会将伪类的四个状态都书写，我们只需要设置鼠标访问状态:hover即可；

01、统一设置一个超链接a的样式，表示我们四个状态的样式都一致；

02、然后通过样式覆盖的原理，设置鼠标访问:hover的样式即可；

```html
    <style>
        /*01、设置a的四个状态link、visited、hover、active的样式都一致 */
        .nav li a {
            font-style: 18px;
            color: #333;
        }

        /* 02、单独设置鼠标访问经过的样式覆盖前面的样式即可 */
        .nav li a:hover {
            color: red;
        }
    </style>
    <div class="nav">
        <ul>
            <li><a href="#">首页</a></li>
            <li><a href="#">产品分类</a></li>
            <li><a href="#">联系我们</a></li>
        </ul>
    </div>
```

#### focus伪类选择器

用于选取获表单元素的焦点，一般input表单或者文本域textarea才能获取该焦点；

```html
    <style>
        input:focus {
            background: springgreen;
        }

        textarea:focus {
            background-color: thistle;
        }
    </style>

    <input type="text">
    <textarea cols="30" rows="10"></textarea>
```

#### ::placeholder占位符的颜色修改（死了都要记）

我们只能用这样方法修改占位符的颜色，其他样是不能 在这里修改；

```css
        input::placeholder {
            color: red;
        }
```

1

## 三、背景属性background

background是一个复合属性，可以用用来设置背景颜色。背景图片等操作；

### 背景颜色（bgc）*background-color*

用来设置元素的背景颜色，取值可以是预定义的英文，16进制取值，rgb取值；

```css
    /* 预定义英文 */
    background-color: red;
    /* 16进制 */
    background-color: #f00;
    /* rgb取值 */
    background-color: rgb(255,0,0);
```

### 背景图（bgi） *background-image*

用来设置元素的背景图片，必须要配合url属性值获取背景图片的路径；

```css
    background-image: url(./img/gAT.gif);
```

### 背景图的平铺方式（bgr）background-repeat

插入背景图以后背景图默认是平铺的，我们可以通过*background-repeat*设置不同的取值实现背景图是否平铺；

01、取值为repeat，是默认的取值，背景图会平铺；

```css
background-repeat: repeat;
```

**02、取值为no-repeat，设置背景图不平铺；**

```css
background-repeat: no-repeat;
```

03、可以单独设置水平或者垂直方的单一平铺，取值为repeat-x或者repeat-y

```css
    /* 水平方向平铺 */
    background-repeat: repeat-x;
    /* 垂直方向平铺 */
    background-repeat: repeat-y;
```

### 背景位置设置（bgp）*background-position*

#### 基本语法

设置背景图在元素中的位置

![](assets/02.png)

默认取值为0,0，表示背景图就在元素的左上角；

```css
background-position: 0 0;
```

#### 取值为方位名词（了解）

水平方向：left、center、right；

垂直方向：top、center、bottom；

```css
     /* 左下角 */
     background-position: left bottom;
     /* 左上角 */
     background-position: left top;
     /* 右下角 */
     background-position: right bottom;
     /* 右上角 */
     background-position: right top;

     /* 顶部和底部水平居中  */
     background-position: center top;
     background-position: center bottom;
     /* 左侧和右侧垂直居中 */
     background-position: left center;
     background-position: right center;

     /* 水平垂直居中 */
     background-position: center center;
     /* 简写 */
     background-position: center;

```

#### 取值为实际像素

取值为两个实际像素，让背景图在我们预定义好的位置显示；

```css
background-position: 100px 100px;
```

如果取值为一个值，那么这个值是表示左右的水平位置，垂直方向的位置默认居中显示；

```css
 background-position: 80px;
```

#### 取值为百分比

取值为百分计算的值是按照父级盒子宽高计算的；

```css
background-position: 50% 50%;
```

如果取值为一个值，那么这个值是表示左右的水平位置，垂直方向的位置默认居中显示；

### 背景固定（bga）background-attachment 

设置背景图片是否跟随内容滚动；

**默认取值scroll滚动**

```css
background-attachment: scroll；
```

**不滚动 fixed**

```css
background-attachment: fixed；
```

### 背景属性综合写法1（死了都要记）	

**基本语法**

![](assets/08.png)

注意：01、属性值没有书写顺序，没有的属性可以省略不写；
           02、属性值和属性值之间用空格隔开；

```css
  /* background-color: magenta; */
  /* background-image: url(./img/icon.png); */
  /* background-repeat: no-repeat; */
  /* background-position: 5px center; */
  /* background: 背景颜色   背景图片地址   背景平铺   背景图像滚动   背景图片位置; */
  background: magenta url(./img/icon.png) no-repeat 5px center;
```

### 背景尺寸设置（bgs）*background-size*

如果背景图片小于当前的盒子或者大于当前的盒子，就需要设置背景图的尺寸大小；

#### 取值为cover（常用）

背景图等比缩放，一直到铺满整个盒子

```css
background-size: cover;
```

**注意：**该属性取值如果**背景图和盒子比例不一致**。可能会导致背景图过大超出盒子显示不全，溢出隐藏；

#### 取值为contain 

背景图等比缩放，直到背景图的宽或者高和盒子一致就停止缩放

```css
background-size: contain;
```

**注意：**该属性取值如果背景图和盒子比例不一致可能会导致背景图不会完全铺满盒子；

#### 取值为实际像素大小和百分比（移动端小图标常用）

设置背景图大小固定，一般我们可以让宽度固定的值，然后让高为auto自动计算

```css
background-size: 45px auto;
```

案例：苏宁易购移动端小图标

### 背景属性综合写法2（了解）

语法

![](assets/10.png)

我们也可以把背景尺寸设置给到综合写法中，用 / 隔开连接即可，但是**必须要有background-position值连写，哪怕是0也要书写，否则综合写法失效**；

```css
background: red url(./img/01.gif) no-repeat 0 0 / cover;
```

**实际开发中我们建议分开写，不容易出错哦！**并且如果background-position值为0就可以直接省略；

```css
/* background: red url(./img/01.gif) no-repeat 0 0 / cover; */
background: red url(./img/01.gif) no-repeat;
background-size: cover;
```

## 四、背景颜色透明rgba（死了都要会）

我们可以设置背景颜色的透明度从而实现透明效果；

**语法： rgba(red, green, blue, alpha)**

alpha取值为0-1之间，0表示完全透明，1表示不透明，之间的数字表示透明的程度

```css
background-color: rgba(0,0,0,.5);
```

**注意：**rgba只能设置背景颜色透明不会影响盒子里面的内容透明；

![](assets/11.png)

## 五、盒子透明opacity

**语法： *opacity*: 透明值；**

opacity 设置盒子的透明，取值为0-1之间，0表示完全透明，1表示不透明，之间的小数表示透明的程度

```css
 opacity: .5;
```

**注意：**用opacity 设置透明，不仅让背景颜色透明，也会影响盒子里面的内容也跟着透明，所以我们不建议使用，后期在制作css3的动画时会用到；

![](assets/12.png)

## 六、css3过渡动画（死了都要记） 

**语法：transition: 属性   时间  运动曲线 延时;**

> ```
> 属性：需要改变过渡的属性
> 时间：整个过渡动画需要多长时间完成
> 运动曲线 ：动画运动形式默认取值为ease。匀速运动linear；
> 延时：鼠标移入需要等待一段时间再去加载过渡动画；
> ```

**实际开发中一般只会调用属性和时间**

```
transition: 属性   时间；
```

> **注意：**
> 01、同时修改多个属性，需要用英文逗号隔开
> 	transition: width 1s, background-color 1s, height 1s;
> 02，**用逗号隔开书写多个属性过渡太麻烦，我们只需要用一个all表示所有的属性即可**
> 	**transition: all 1s ；**
> 03、**过渡加在本身上，谁做动画给谁加；**



## 七、css3常用新属性（死了都要会）

### **圆角*border-radius***

#### 圆角矩形

*border-radius*取值为一个实际像素

```css
        .box {
            width: 300px;
            height: 100px;
            background-color: #f00;
            border-radius: 15px;
        }
```

![](../../css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/14.png)

#### 圆形

矩形必须是正方形，设置border-radius取值大于等于高度一半或者直接设置50%

```css
        .box {
            width: 100px;
            height: 100px;
            background-color: #f00;
            /* border-radius: 50px; */
            border-radius: 50%;
        }
```

![](../../css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/15.png)

#### 胶囊形状

矩形必须是长方形，设置border-radius取值大于等于高度一半；

![](../../css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/16.png)

```css
        .box {
            width: 300px;
            height: 50px;
            background-color: #f00;
            border-radius: 25px;
        }
```

如果设置border-radius*取值为50%，会绘制椭圆

![](../../css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/17.png)

```
        .box {
            width: 300px;
            height: 50px;
            background-color: #f00;
            border-radius: 50%;
        }
```

#### 半圆

设置border-radius取值个数为4个值：分别是：**左上角  右上角  右下角 左下角**

语法：**border-radius：左上角  右上角  右下角 左下角；**

```
        .box {
            width: 100px;
            height: 100px;
            background-color: #f00;
            border-radius: 0 50px 50px 0;
        }

        .box1 {
            width: 100px;
            height: 100px;
            background-color: #f00;
            border-radius: 50px 0 0 50px;
        }
```

![](../../css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/18.png)

### 盒子阴影box-shadow

**语法**

```
box-shadow: h-shadow v-shadow blur spread color inset;
box-shadow:水平阴影   垂直阴影   模糊距离   阴影大小   阴影颜色  内/外阴影；
```

**水平阴影：**   阴影在盒子的水平方向左右的位置设置；
**垂直阴影：**   阴影在盒子的垂直方向上下的位置设置；
**模糊距离：**   阴影的羽化模糊的程度，值越大越模糊；
**阴影大小：**   设置阴影的大小尺寸，一般可以不设置，有了需求在设置；
**阴影颜色： **  阴影的颜色显示；
**内/ 外阴影：**阴影在盒子的内部显示还是外部显示，默认不设置是外部阴影，想要设置内阴影就设置取值为inset；

**注意：一个盒子可以加多个阴影，用个英文的逗号隔开即可**

```css
box-shadow: 5px 5px 10px #000, 20px 20px 10px red;
```

### 文字阴影	

**语法：text-shadow：**

```
	text-shadow: h-shadow v-shadow blur color;
	text-shadow:水平阴影   垂直阴影   模糊距离   阴影颜色 ；
```

参数和盒子阴影差不多； 

**案例：实现凹凸文字效果：**

![](../../css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/19.png)

## 八、光标类型cursor（了解）

默认的小箭头 

```css
cursor: default;
```

小手形状

```css
cursor:pointer;
```

移动图标

```css
cursor:move;
```

文本图标

```css
cursor:text;
```

禁止点击图标

```css
cursor:not-allowed;		
```



## 九、案例

01、成长守护平台案例完成；

![](assets/03.png)

02、超大背景图插入；

03、购物车案例完成

![](assets/04.png)

04、苏宁易购移动端底部图标

![](assets/09.png)



## 十、作业

**01、it资讯★★★★★ [it资讯.psd](..\作业\01 it资讯\it资讯.psd) **

![](assets/05.png)

**02、综合练习(选做)★★**

![](assets/07.png)

**03、Google搜索★★★★★ **

> 最外层大盒子google宽度1200px，水平居中；
>
> logo盒子中图片居中；
>
> 搜索盒子search宽561px，高44px，水平居中margin: 50px auto;
>
> 搜索盒子中嵌套input控件，宽561px，高44px，文字首行缩进50px距离，实现胶囊形状，加盒子阴影
>
> 搜索小图标用背景图插入bgp取值水平方向20px，垂直居中；

![](img/Google.jpeg)



















































































































































































































































































































23
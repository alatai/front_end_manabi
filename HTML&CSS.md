## HTML&&CSS

### 元素类型

*根据元素的显示类型，HTML 元素可以主要分为两大类*

#### 块级元素（block-level element）

独占父级元素一行

```html
div p h pre ul ol form...
```

#### 行内级元素（inline-level element）

多个行内级元素可以在父元素的同一行显示

```html
a img span label code input...
```



*根据元素的内容类型，HTML 元素可以主要分为 2 大类*

#### 替换元素（replaced element）

元素本身没有实际内容，浏览器根据元素的类型和属性，来决定元素的具体显示内容

```html
img input iframe vide...
```

#### 非替换元素（non-replaced element）

和替换元素相反，元素本身是有实际内容的，浏览器会直接将其内容显示出来，而不需要根据元素类型和属性来判断到底显示什么内容

```html
div p pre h1~h6 ul ol...
```



#### 小结


| 显示类型   | 内容类型   | 例                        | 特征                                                         |
| :--------- | :--------- | :------------------------ | :----------------------------------------------------------- |
| 块级元素   | 替换元素   |                           |                                                              |
|            | 非替换元素 | div p pre h1~h6...        | 独占父元素一行，可以随意设置宽高，高度默认由内容决定         |
| 行内级元素 | 替换元素   | img input iframe video... | 跟其他行内级元素在同一行显示，可以随意设置宽高               |
|            | 非替换元素 | a strong span code...     | 跟其他行内级元素在同一行显示，不可以随意设置宽高，宽高由内容决定 |



### CSS 使用

#### 引入方式

* 内联样式
* 文档样式表
* 外部样式表

#### 其他细节

* @import
* @charset
* 加载顺序



### 优先级

哪个 CSS 属性会生效，取决于 CSS 属性所处环境的优先级

* 针对性越强的选择器，优先级越高
* 如果优先级一样，就参考就近原则

理解层叠，重要性排序 ①重要程度 ②优先级 ③资源顺序

**!important 可覆盖所有优先级**



#### 控制继承

* inherit

  子元素属性同父元素相同，设置属性的 inherit，可以强制继承

  `width height margin padding border` 是不会被继承

  **CSS 属性继承的是计算值，并不是当初编写属性时的指定值**

* initial

  设置属性值和浏览器默认样式相同，如果浏览器默认样式中未设置且该属性是自然继承的，那么会设置为initial

* unset

  将属性重置为自然值

重设所有属性，CSS 的 ```shorthand``` 属性 ```all``` 可以用于同时将这些继承值中的一个应用于几乎所有属性

​	```all: inherit/initial/unset/revert/inherit/initial```



#### CSS 属性使用经验

为何有时候编写的 CSS 属性不好使，有可能因为

* 选择器的优先级太低
* 选择器没选中对应的元素
* CSS 属性的使用形式不对
  * 元素不支持此 CSS 属性，比如 ```span``` 默认是不支持 ```width```
  * 浏览器不支持此 CSS 属性，比如旧版的浏览器不支持 CSS3 
  * 被同类型的 CSS 属性覆盖，比如 font 覆盖 font-size



### 颜色

* RGB 颜色
* 十六进制颜色
* RGBA



### CSS 选择器

#### 常见选择器

* 通用选择器

  ```css
  * {
  	/* TODO */  
  }
  ```

* 元素选择器、标签选择器

  ```css
  div {
  	/* TODO */
  }
  ```

* id 选择器

  ```css
  #title {
  	/* TODO */	
  }
  ```

* 属性选择器

  ```css
  [href="#top"] {
  	/* TODO */
  }
  ```

* 后代选择器

  ```css
  div span {	/* TODO */}
  ```

* 子选择器

  ```css
  div>span {	/* TODO */}
  ```

* 相邻兄弟选择器

  ```css
  div+p {	/* TODO */}
  ```

* 全体兄弟选择器

  ```css
  div~p {	/* TODO */}
  ```

* 交集选择器

  ```css
  div.one#title {	/* TODO */}
  ```

* 并集选择器

  ```css
  div, .one, #title {	/* TODO */}
  ```

#### 伪类

为了通过选择器，格式化 DOM 树以外的信息，以及不能被常规 CSS 选择器获取的信息

* 动态伪类

  ```css
  a:link /* 未访问的链接 */a:visited /* 已访问的链接 */a:hover /* 当鼠标移动到链接上 */a:active /* 当鼠标左键单击链接不松开 */a:focus /* 当链接呗[tab]键选中激活时 */:hover :active :focus 还可以应用到其他元素上
  ```

* 结构伪类

  ```css
  :nth-child(an+b):nth-last-child(an+b):nth-of-type(an+b):nth-last-of-type(an+b)
  ```

* 否定伪类

  ```css
  not(选择器){	/* TODO */}
  ```

#### 伪元素

可以创建一些文档语言无法创建的元素，为了弥补 CSS 选择器的不足，用来更方便地获取信息（本质上创建了虚拟容器\元素）

```css
::first-line::first-letter::before::after
```

**伪元素使用注意**

* ```::before``` 和 ```::after``` 的 content 属性不能少
* ```::before``` 和 ```::after``` 的 display 默认是 inline，可以把 ```::before``` 和 ```::after``` 当作 span 元素
* 可以使用 ```::before``` 和 ```::after```  来取代子元素
* ```::before``` 和 ```::after``` 是 CSS 样式，所以可有可无的内容才使用



### 常用属性

#### 文字相关

* text-decoration
* spacing
* text-transform
* text-indent
* text-align
* font-size
* font-family
* @font-face
* font-weight
* font-style
* font-variant



#### CSS 属性 - text-overflow

通常用来设置文字溢出时的行为，处理不可见的内容

* clip：溢出的内容直接裁剪掉（字符可能会显示不完整）
* ellipsis：溢出那行的结尾处用省略号表示
* text-overflow 生效的前提是 overflow 不为 visible
* text-overflow 的效果受 direction 的影响



#### CSS 属性 - white-space

用于设置空白处理和换行规则

|            | New Lines | Spaces and Tabs | Text Wrapping |
| ---------- | --------- | --------------- | ------------- |
| 'normal'   | Collapse  | Collapse        | Wrap          |
| 'pre'      | Preserve  | Preserve        | No wrap       |
| 'nowrap'   | Collapse  | Collapse        | No wrap       |
| 'pre-wrap' | Preserve  | Preserve        | Wrap          |
| 'pre-line' | Preserve  | Collapse        | Wrap          |

* normal：合并所有连续的空白，允许单词超屏时自动换行
* nowrap：合并所有连续的空白，不允许单词超屏时自动换行
* pre：阻止合并所有连续的空白，不允许单词超屏时自动换行
* pre-wrap：阻止合并所有连续的空白，允许单词超屏时自动换行
* pre-line：合并所有连续的空白（但保留换行），允许单词超屏时自动换行



#### CSS 属性 - display

能修改元素的显示类型，有 4 个常用属性值

* block 让元素显示为块级元素
* inline 让元素显示为行内级元素
* none 隐藏元素
* inline-block 让元素同时具备行内级、块级元素的特征



其中**inline-block**同时具备行内级、块级元素的特征

​	跟其他元素在同一行显示，可以随时设置宽高，宽高由内容决定

可以理解为

​	对外来说，它是一个行内级元素

​	对内来说，它是一个块级元素



##### 常见用途

​	让行内级非替换元素（a、span 等）能够随意设置宽高

​	让块级元素（div、p 等）能够跟其他元素在同一行显示



##### 元素之间的空格问题

行内级元素（包括 inline-block 元素）的代码之间如果有空格，会被解析显示为空格，解决方案

* 内容紧贴显示
* 设置浮动
* 设置父元素的 ```font-size: 0```，然后在元素中重新设置自己需要的 ```fonot-size```

**注意**

* 不要使用行内级元素去包含块级元素
* 块级元素、inline-block，理论上可以包含其他任何元素 
* 行内级元素（a span strong 等）一般情况下，只能包含行内级元素



#### CSS 属性 - visibility

能控制元素的可见性，有 2 个常用属性值

* visible 显示元素
* hidden 隐藏元素

**hidden 和 none 的区别**

* hidden 虽然元素看不见了，但元素的框依旧还留着，还会占着原来的位置
* none 不仅元素看不见了，元素的框也不会留着，不会占着原来的位置



#### CSS 属性 - line-height

用于设置文本的最小行高（简单理解为，一行文字所占据的高度）

**严格定义：**两行文字基线（base-line）之间的间距（两行文字顶部的间距）

应用实例：假设 div 中只有一行文字，如何让这行文字在 div 内部垂直

````line-height: 等于 height 的值````



#### CSS 属性 - box-shadow

* 第 1 个属性值：水平方向的偏移，正数往右偏移
* 第 2 个属性值：垂直方向的偏移，正数往下偏移
* 第 3 个属性值：模糊半径（blur radius）
* 第 4 个属性值：延伸半径



#### CSS 属性 - transition

让所有可动画面效果都在给定时间变化

```css
transition: all 0.25s;
```



#### CSS 属性 - background-image

用于设置元素的背景图片

* 会覆盖在 backgroud-color 上面
* 在图片的透明区域，可以看到背景色
* 如果设置了多张图片，设置的第一张将显示在最上面，其他图片按顺序层叠在下面

**注意**

如果设置了背景图片后，元素没有具体的宽高，背景图片是不会显示出来的

padding 不会影响背景图片的位置



##### 滑动门技术

非纯色背景了，带圆角等特殊效果



##### 图片适配显示

* 先做一张最大的图片（设置最小宽度 min-width，包含最主要内容让小屏幕也可以显示）

* 舍弃不重要的内容（按照原来大小居中显示）

##### background-image 和 img 的选择

利用 background-image 和 img 都能实现显示图片的需求

|                        | img                | background-image       |
| ---------------------- | ------------------ | ---------------------- |
| 性质                   | HTML 元素          | CSS 样式               |
| 图片是否占用空间       | ✔️                  | ❌                      |
| 浏览器右击直接查看地址 | ✔️                  | ❌                      |
| 支持 CSS Sprite        | ❌                  | ✔️                      |
| 更有可能被搜索引擎收录 | ✔️（结合 alt 属性） | ❌                      |
| 加载顺序               | 优先加载           | 等加载完 HTML 后再加载 |

**总结**

* img，作为网页内容的重要组成部分，比如广告图片、LOGO 图片、文章配图、产品图片
* background-image，可有可无。有能让网页更加美观，没有也不影响用户获取完整的网页内容信息

**宗旨：**在没有任何 CSS 样式的情况下，用户也能浏览到网页中完整的内容信息



#### CSS 属性 - background-atttachement

常用属性值

* scroll 背景图片跟随元素一起滚动（默认值）
* local 背景图片跟随元素以及元素内容一起滚动
* fixed 背景图片相对于浏览器窗口固定（常用在平铺背景）



### CSS Sprite

一种 CSS 图像合成技术，将各种图片合并到一张图片上，然后利用 CSS 背景定位来显示对应的部分

**使用 CSS Sprite 的好处**

* 减少网页的 http 请求数量，加快网页响应速度，减轻服务压力
* 减少图片总大小
* 解决了图片命名的困扰，只需要针对一张集合的图片命名
* 更换风格方便，只需要在少数几张图片上修改图片的颜色或样式，整个网页的风格就可以改变



### 盒子模型

HTML 中的每一个元素都可以看做是一个盒子，缩写时顺时针方向（上、右、下、左）

#### 上下 margin 传递问题

**margin-top 传递**

如果**块级元素**的顶部线和**块级父元素**的顶部线重叠，那么这个块级元素的 ```margin-top``` 值会传递给父元素

**margin-bottom 传递**

如果**块级元素**的底部线和**块级父元素**的底部线重叠，并且父元素的高度是 auto，那么这个块级元素的 ```margin-bottom``` 会传递给父元素



#### 解决上下 margin 传递问题

* 给父元素或子元素设置 ```inline-block```
* 给父元素加 ```padding-top``` 或者 ```padding-bottom```
* 给父元素设置 ```border```

**建议**

* margin 一般是用来设置兄弟元素之间的距离
* padding 一般是用来设置父子元素之间的距离



#### 上下 margin 折叠问题

垂直方向上相邻的 2 个 margin （margin-top margin-bottom）有可能合并为 1 个margin，这种现象叫做 **collapse(折叠)**

水平方向上的 margin（margin-left margin-right）永远不会 collapse



#### 折叠后的计算规则

* 如果都是整数，最终值为：绝对值最大的那个正数值
* 如果都是负数，最终值为：绝对值最大的那个负数值
* 如果正、负都有，最终值是：最大正数和最小负数相加



#### 如何防止 collapse

* 只设置其中一个元素的 margin
* 条件允许的话，使用 padding 取代 margin



#### 行内级非替换元素的注意点

* 以下属性对行内级非替换元素不起作用

  ```css
  width height margin-top margin-bottom...
  ```

* outline 在 border 外，不占空间



#### 水平居中常用设置

* 行内级元素、inline-block 元素想要在父元素中，给父元素设置 ```text-align: center```
* 块级元素想要在父元素中水平居中，给这个块级元素设置 ```margin: 0 auto```



### 定位

#### 文档画布背景

没有 HTML 元素对应着文档画布，如何设置文档画布背景？

​	HTML 或者 body 元素的背景都能够延伸到整个文档画布

**Normal Flow：**标准流（从左到右，从上到下；互相之间不存在层叠）

**比较明显的缺点**

* 设置一个元素的 margin 或者 padding，通常会影响到标准流中其他元素的定位效果
* 不便于实现元素层叠的效果



#### CSS 属性 - position

利用 position 可以对元素进行定位，常用属性值

* static 静态定位
* relative 相对定位
* absolute 绝对定位
* fixed 固定定位



##### relative 相对定位

定位参照对象是元素自己原来的位置，进行相对定位的元素还在标准流当中（原来占用着的位置还在）

相对定位一般用于对元素进行微调，在不影响其他元素的情况下

**使用技巧：**利用 margin-left 和 left 属性的值完成水平相加减操作

```css
xxx {	margin-left: -960px;	left: 50%;}
```



##### flxed 固定定位

元素脱离 normal-flow，定位参照对象是视口（viewport）

**画布和视口**

* 视口（viewport）文档的可视区域（可简单理解为浏览器窗口的可视区域）
* 画布（canvas）用于渲染文档的区域，文档内容超出视口范围
* 宽高对比：画布 >= 视口



##### static 静态定位

position 属性的默认值，按 normal-flow 定位



##### absolute 绝对定位

元素脱离 normal-flow，可以通过 left、right、top、bottom 进行定位

* 定位参照对象是最邻近的定位祖先元素
* 如果找不到这样的祖先元素，参照对象是视口



##### 脱标元素的特点

* 可以随意设置宽高
* 宽高默认由内容决定
* 不再受标准流约束
  * 不再严格按从上到下、从左到右排布
  * 不再严格区分块级、行内级，块级、行内级的很多特征会消失
* 不再给父元素汇报宽高数据
* 脱标元素内部默认还是按照标准流布局



##### 定位元素（positioned element）

position 值不为 static 的元素

在绝大数情况下，子元素都是需要相对于父元素进行定位

如果希望子元素都是需要相对父元素进行定位，又不希望父元素脱标

**常用解决方案**

* 父元素设置 relative
* 子元素设置 absolute



##### 小结

|                   | 脱离标准流 | 定位元素 | 绝对定位元素 | 参照对象         |
| ----------------- | ---------- | -------- | ------------ | ---------------- |
| static 静态定位   | ❌          | ❌        | ❌            | ❌                |
| relative 相对定位 | ❌          | ✔️        | ❌            | 元素自己原来位置 |
| absolute 绝对定位 | ✔️          | ✔️        | ✔️            | 邻居的定位元素   |
| fixed 固定定位    | ✔️          | ✔️        | ✔️            | 视口             |



#### 元素的层叠

| 关系       | 元素             | 效果                             |
| ---------- | ---------------- | -------------------------------- |
| 父子关系   |                  | 子元素会层叠在父元素上面         |
|            | 都是非定位元素   | 在标准流中不存在层叠现象（默认） |
| 非父子关系 | 1 个是定位元素   | 定位元素会层叠在非定位元素       |
|            | 1 个是非定位元素 |                                  |
|            | 都是定位元素     | 使用 CSS 属性 z-index 来控制层叠 |



##### CSS 属性 - z-index

用来设置定位元素的层叠属性（仅对定位元素有效），取值可以是正整数、负整数、0

**比较原则**

* 如果是兄弟关系
  * z-index 越大，层叠在越上面
  * z-index 相等，写在后面的那个元素层叠在上面
* 如果不是兄弟关系
  * 各自从元素自己以及祖先元素中，找出最邻近的 2 个定位元素进行比较
  * 而且这两个定位元素必须有设置 z-index 的具体数值



#### 定位的方案

在 CSS 中，有 3 种常用的方法对元素进行定位、布局

* normal flow 标准流
* absolute position 绝对定位
* float 浮动

绝对定位、浮动都会让元素脱离标准流，以达到灵活布局的效果



#### 浮动

##### 浮动的规则

* 元素一旦浮动后

  * 脱离标准流
  * 朝着向左或向右的方向移动，直到自己的边界紧贴着包含块（一般是父元素）或者其他浮动元素的边界为止

* 浮动元素的顶端不能超过包含块的顶端，也不能超过之前所有浮动元素的顶端

  

##### 定位元素会层叠在元素上面

* 浮动元素不能与行内级内容层叠，行内级内容将会被浮动元素推出（利用此特征，可以轻松实现文字环绕功能）
  * 比如行内级元素、inline-block 元素
* 行内级元素、inline-block 元素浮动后，其顶部将于所在行的顶部对齐



##### 浮动元素之间不能层叠

* 如果一个元素浮动，另一个浮动元素已经在那个位置了，后浮动的元素将紧贴着前一个浮动元素
* 如果水平方向剩余的空间不够显示浮动元素，浮动元素将向下移动，直到有充足的空间为止



##### 浮动的应用

常用场景

* 解决行内级元素、inline-block 元素的水平间隙问题
* 布局



##### 浮动存在的问题

* 由于浮动元素脱离标准流，变成了脱标元素，所以不再向父元素汇报高度
* 导致了父元素高度塌陷的问题
* 解决父元素高度坍塌问题的过程，一般叫做清浮动（清理浮动）

**清浮动的常见方法**

* 给父元素设置固定高度
  * 拓展性不好，不推荐
* 让父元素浮动
  * 可能导致页面中所有元素都浮动
  * 父元素脱离了标准流，不推荐
* 让父元素成为绝对定位元素（position 设置为 absolute 或 fixed）
  * 父元素脱离了标准流
  * 改变了元素的盒子特性，不推荐
* 给父元素设置 display 为 inline-block、inline-table、table、table-cell、table-caption
  * 改变了父元素的盒子特性，不推荐
* 给父元素设置 overflow 为 visible 以外的值（hidden、auto、scroll）
  * 改变了父元素对内容溢出的默认行为，不推荐

**CSS 属性 - clear**

一般就只用在费浮动元素上，可以让非浮动元素与浮动元素不层叠

**最终解决方案**

```css
xxx::after {	content: "";	display: block;	clear: both;	height: 0; /* 兼容旧浏览器 */	visibility: hidden; /* 兼容就浏览器 */}xxx::after {	*zoom: 1; /* 兼容 IE6~7 */}
```



#### 定位方案对比

| 定位方案                      | 应用场景 |
| ----------------------------- | -------- |
| normal flow（标准流）         | 垂直布局 |
| absolute position（绝对定位） | 层叠布局 |
| float（浮动）                 | 水平布局 |



#### 常用网站结构

* header
  * LOGO/导航/搜索框/登录注册/slogan
* main
  * 核心内容/产品内容
* footer
  * 友情链接/网站备案/版权信息/其他...



### 浏览器私有前缀

有时候可能看到有些 CSS 属性名前面带有：-o-、-xv-、-ms-、mso-、-moz-、-webkit-

```css
-o-animation-duration: 2s;mso-background: red;-webkit-background-clip: border-box;-moz-background-size: contain;-ms-word-wrap: normal;
```

**上述前缀叫做浏览器私有前缀，只有对应的浏览器才能解析使用**

* -o-、-xv-、：Opera 等
* -ms-、mso-：IE 等
* -moz-：Firefox 等
* -webkit：Safari、Chrome 等

**官方文档给出的专业术语叫做：vendor-specific extensions（供应商特定拓展）**

**浏览器私有前缀是浏览器对新 CSS 属性的一种提前支持**



### flex 布局

flex 布局（Flexible 布局，弹性布局）是在小程序开发经常适用的布局方式

* 开启了 flex 布局的元素叫 flex container

* flex container 里面的直接子元素叫 flex items

**设置 display 属性为 flex 或者 inline-flex 可以成为 flex container**

* flex：以 block-level 形式存在
* inline-flex：以 inline-block 形式存在



**应用在 flex container 上的 CSS 属性**

* flex-flow
* flex-direction
* flex-wrap
* justify-content
* align-items
* align-content



**应用在 flex items 上的 CSS 属性**

* flex
* flex-grow
* flex-basis
* flex-shrink
* order
* align-self



#### flex 布局模型

![image-20200816162132501](/Users/qipeng/Library/Application Support/typora-user-images/image-20200816162132501.png)

#### flex-direction

**flex items** 默认都是沿着 main axis（主轴）从 main start 开始往 main end 方向排布

**flex-direction** 决定了 main axis 的方向，有 4 个取值

* row（默认值）
* row-reverse
* column
* column-reverse



#### justify-content

**justify-content** 决定了 flex items 在 main axis 上的对齐方式

* flex-start（默认值）：与 main start 对齐
* flex-end：与 main end 对齐
* center：居中对齐
* space-between：flex items 之间的距离相等，与 main start、main end 两端对齐
* space-evenly：flex items 之间的距离相等，flex items 与 mian start、main end 之间的距离等于 flex items 之间的距离
* space-around：flex items 之间的距离相等，flex items 与 mian start、main end 之间的距离是 flex items 之间的距离的一半



#### align-items

**align-items** 决定了 flex items 在 cross axis 上的对齐方式

* stretch（默认值）：当 flex items 在 cross axis 方向的 size 为 auto 时，会自动拉伸至填充 flex container
* flex-strat：与 cross start 对齐
* flex-end：与 cross end 对齐
* center：居中对齐
* baseline：与基准线对齐



#### flex-wrap

**flex-wrap** 决定了 flex container 是单行还是多行

* nowrap（默认值）：单行
* wrap：多行
* wrap-reverse：多行（对比 wrap、cross start 与 cross end 相反）



#### flex-flow

**flex-flow** 是 **flex-direction || flex-wrap** 的简写

```css
flex-flow: column wrap;/* 等价于 */flex-direction: column;flex-wrap: wrap;flex-flow: row-reverse;/* 等价于 */flex-direction: row-reverse;flex-wrap: norwrap;flex-flow: wrap;/* 等价于 */flex-direction: row;flex-wrap: wrap;
```



#### align-content

**align-content** 决定了多行 flex items 在 cross axis 上的对齐方式，用法与 justify-content 类似

* stretch（默认值）：与 align-items 的 stretch 类似
* flex-start：与 cross start 对齐
* flex-end：与 cross end 对齐
* center：居中对齐
* ...



#### order

**order** 决定了 flex items 的排布顺序

* 可以设置任意整数（正整数、负整数、0），值越小就越排在前面
* 默认值是 0



#### align-self

flex items 可以通过 **align self** 覆盖 flex container 设置的 align-items

* auto（默认值）：遵从 flex container 的 align-items 设置
* stretch、flex-start、flex-end、center、baseline，效果跟 align-items 一致



#### flex-grow

**flex-grow** 决定了 flex items 如何拓展

* 可以设置任意非负数字（正小数、正整数、0），默认值是 0
* 当 flex container 在 main axis 方向上有剩余 size 时，flex-grow 属性才会有效
* 如果所有 flex items 的 flex-grow 总和 sum 超过 1，每个 flex item 扩展的 size 为
  * flex container 的剩余 size*flex-grow/sum
* 如果所有 flex items 的 flex-grow 总和 sum 不超过 1，每个 flex item 扩展的 size 为
  * flex container 的剩余 size*flex-grow
* flex items 扩展后的最终 size 不能超过 max-width、max-height（与主轴有关）



#### flex-shrink

**flex-shrink** 决定了 flex items 如何收缩

* 可以设置任意非负数字（正小数、正整数、0），默认值是 1
* 当 flex items 在 main axis 方向上超过了 flex container 的 size，flex-shrink 属性才会生效
* 如果所有 flex items 的 flex-shrink 总和 sum 超过 1，每个 flex item 收缩的 size 为
  * flex items 超出 flex container 的 size * 收缩比例/所有 flex items 的收缩比例之和
* 如果所有 flex items 的 flex-shrink 总和 sum 不超过 1，每个 flex item 收缩的 size 为
  * flex items 超出 flex container 的 size * sum * 收缩比例/所有 flex items 的收缩比例之和
* 收缩比例 = flex-shrink * flex item 的 base size
  * base size 就是 flex item 放入 flex container 之前的 size
* flex items 收缩后的最终 size 不能小于 min-width、min-height（与主轴有关）



#### flex-basis

**flex-basis** 用来设置 flex items 在 main axis 方向上的 base size

* auto（默认值）、content：取决于内容本身的 size
* 决定 flex items 最终 base size 的因素，从优先级高到低
  * max-width、max-height、min-width、min-height（与主轴有关）
  * flex-basis
  * width、height（与主轴有关）
  * 内容本身的 size



#### flex

**flex** 是 **flex-grow flex-shrink || flex-basis** 的简写

* 默认值是 0 1 auto
* none：0 0 auto


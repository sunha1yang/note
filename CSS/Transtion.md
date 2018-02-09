## Transition

### 什么是Transition？
CSS3的transition允许CSS的属性值在一定的时间区间内平滑地过渡。这种效果可以在鼠标点击、获取焦点、被点击或对元素任何改变中触发，并平滑地以动画效果改变CSS的属性值。


### 使用CSS创建简单过渡的步骤：
1. 在默认样式中声明元素的初始状态样式
2. 声明过渡元素最终状态样式
3. 在默认样式中通过添加过渡函数，添加一些不同的样式


### 过渡属性
> 过渡transition是一个复合属性，包括`transition-property`、`transition-duration`、`transition-timing-function`、`transition-delay`这四个子属性。通过这四个子属性的配合来完成一个完整的过渡效果。


**四个子属性的简单介绍**
|属性名|属性作用|
|-|-|
|transition-property|过渡或动态模拟的CSS属性(默认值为all)|
|transition-duration| 完成过渡所需要的时间(默认值为0s)|
|transiton-timing-function|过渡函数(默认值为ease函数)|
|transition-delay| 过渡开始出现的延迟时间(默认值为0s)|


过渡语法可以简单的这样写：

```
transition： <transition-property> || <transition-duration> || <transition-timing-function> || <transition-delay>
```



### 过渡属性介绍：
#### **transition-property**
用trasition-property来指定过渡属性，但是并不是所有的CSS样式值都可以过渡，只有具有中间值的属性才具备过渡效果。

> 值：none | all | single-transition-property  [, single-transition-property] *
> 初始值：all

##### 值的介绍
none：没有指定任何样式
all：默认值，表示指定元素所有支持transition-property属性的样式
single-transition-property：可过渡的样式，可用逗号分开写多个样式

##### 可过渡的样式
1. 颜色： color background-color border-color outline-color
2. 位置： backround-position left right top bottom
3. 长度： 
    [1]max-height min-height max-width min-width height width
    [2]border-width margin padding outline-width outline-offset
    [3]font-size line-height text-indent vertical-align  
    [4]border-spacing letter-spacing word-spacing
4. 数字： opacity visibility z-index font-weight zoom
5. 组合： text-shadow transform box-shadow clip
6. 其他： gradient

**`想知道更多请戳`**[这里](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties)


#### trasition-duration 
trasition-duration属性主要用来设置一个属性过渡到另一个属性所需要的时间。
> 值：time [, time]*
> 初始值：0s

**注意**
1. 该属性不能为负值
2. 若该属性为0s则为默认值，若为0则为无效值。必须带单位
3. 该值为单值时，即所有过渡属性都对应同样时间；该值为多值时，过渡属性按照顺序对应持续时间


#### 过渡时间函数
过渡时间函数用于指定元素过渡属性随时间变化的过渡速度、过渡期间操作进展情况，可以将某个值指定为预定义函数、阶段函数或者三次博塞尔曲线。

> 值：timing-function [, timing-function] *
> 初始值：ease


函数分为三种：
1. 单一的过渡函数
2. 三次贝赛尔曲线
3. step函数

##### 单一的过渡函数
1. ease： 开始和结束慢，中间快。相当于cubic-bezier(0.25,0.1,0.25,1)
2. linear： 匀速。相当于cubic-bezier(0,0,1,1)
3. ease-in： 开始慢。相当于cubic-bezier(0.42,0,1,1)
4. ease-out： 结束慢。相当于cubic-bezier(0,0,0.58,1)
5. ease-in-out： 和ease类似，但比ease幅度大。相当于cubic-bezier(0.42,0,0.58,1)


##### 三次贝赛尔曲线
贝塞尔曲线通过p0-p3四个控制点来控制，其中p0表示(0,0)，p3表示(1,1)。而<transition-timing-function>就是通过确定p1(x1,y1)和p2(x2,y2)的值来确定的
`公式：transition-timing-function: cubic-bezier(x1,y1,x2,y2)`

##### step函数

steps步进函数将过渡时间划分成大小相等的时间时隔来运行

steps步进函数语法为:

`steps(integer [,start | end]?)`
integer：用来指定间隔个数(该值只能是正整数)
第二个参数: 该参数可选，默认是end，表示开始值保持一次；若参数为start，表示开始不保持


### 注意事项：
1. transition的多个属性值用`逗号`分隔开表示可以同时为多个值设置过渡属性
2. 若不同的transition-property值，对应的transition-delay | transition-timing-function | transition-duration的属性值都相同时，则对应的这些属性设置一个即可
3. 当transition-property值的个数多于对应的transition-delay | transition-timing-function | transition-duration的属性值(属性值的个数大于1个)时，将按顺序开始取值
4. 当transition-property值的个数少于对应的transition-delay | transition-timing-function | transition-duration的属性值个数时，多余的属性值将无效
5. 当transition-property的值中出现一个无效值，它依然按顺序对应transition的其他属性值(其他属性出现无效值，处理情况也类似)
6. 当transition-property的值中，有些值重复出现多次，则以最后出现的值为准，前面所有出现的值都被认定为无效值，但依然按顺序对应transition的其他属性值
7. 当transition-duration出现无效值时，会到终点值，只是没有过渡效果
8. 当transition-duration小于0时，会到终点值，只是没有过渡效果
9. 当transition-duration + transition-delay的值小于0时，会到终点值，只是没有过渡效果
7. 过渡分为两个阶段：前进(forward)和反向(reverse)。若前进阶段进行一段时间后进入反向阶段，则反向阶段的初始值是前进阶段结束时的瞬时值
8. 以hover为例，若在元素非hover态时设置transition，相当于设置的反向状态。而前进和反向是一致的。而如果在元素hover态设置transition，则前进状态以hover态设置的为准，而反向状态以非hover态设置的为准
9. 如果子元素和父元素过渡属性都一致。若触发子元素过渡时，父元素正在过渡，则将父元素过渡的中间态的值作为子元素过渡的初始值
10. 若过渡起始值或过渡开始值为auto，则浏览器不会自己计算成具体数字值，而是不发生过渡效果。所以要过渡某些属性，首先需要将其重置成具体数字值
11. 隐式过渡是指一个属性改变时引起另一个属性的改变。如border-width是1em，则font-size改变时，border-width也会相应的改变。firefox和IE浏览器支持隐式过渡。而webkit内核浏览器不支持隐式过渡


### 触发方式
1. 过渡transition的触发有三种方式，分别是伪类触发、媒体查询触发和javascript触发


### 过渡事件API
关于过渡transition的事件只有一个，是transitionend事件，它发生在过渡事件完成后

#### 属性
1. `propertyName`：发生transition效果的CSS属性名

2. `elapsedTime`：代表发生实际效果的持续时间。若完整进行，则返回完整时间；若中途中断，则返回实际时间
3.  `pseudoElement`：如果transition效果发生在伪元素，会返回该伪元素的名称，以“::”开头。如果不发生在伪元素上，则返回一个空字符串' '

#### 注意
1. 过渡分为两个阶段：前进阶段和反向阶段。transitionend事件在前进阶段结束时会触发，在反向阶段结束时也会触发
2. 过渡事件触发的次数与transition-property过渡属性的个数有关。过渡属性有几个就会触发几次
3. 如果过渡属性是复合属性，如border-width相当于是border-top-width、border-bottom-width、border-left-width和border-right-width这四个属性的集合。则过渡事件触发4次
4. 如果过渡属性是默认值all，则过渡事件的次数是计算后的非复合的过渡属性的个数。如果发生过渡的属性是border-width和width，则经过计算后过渡事件应该触发5次
5. 如果过渡延迟时间为负值，且绝对值大于等于过渡持续时间时，低版本webkit内核浏览器不会产生过渡效果，但会触发过渡事件；而其他浏览器即不会产生过渡效果，也不会触发过渡事件
6. 如果过渡属性存在复合属性及该复合属性包含的非复合属性，则浏览器计算复合属性的子属性时，不会重复计算已包含的属性




## Animation
CSS animations 使得可以将从一个CSS样式配置转换到另一个CSS样式配置。动画包括两个部分：
1. 描述动画的样式规则
2. 用于指定动画开始、结束以及中间点样式的关键帧。

|属性名|属性介绍|
|-|-|
|animation-name|指定由@keyframes描述的关键帧名称|
|animation-duration|设置动画一个周期的时长|
|animation-timing-function|设置动画速度， 即通过建立加速度曲线，设置动画在关键帧之间是如何变化|
|animation-delay|设置延时，即从元素加载完成之后到动画序列开始执行的这段时间|
|animation-iteration-count|设置动画重复次数， 可以指定infinite无限次重复动画|
|animation-direction|设置动画在每次运行完后是反向运行还是重新回到开始位置重复运行|
|animation-play-state|允许暂停和恢复动画|
|animation-fill-mode|指定动画执行前后如何为目标元素应用样式|



### 关键帧
关键帧 （@keyframes）：在@keyframes中，我们定义动画关键帧，然后animation会按照keyframes关键帧里我们指定的帧状态进行过渡执行

> 语法规则：
> `keyframes-rule: '@keyframes' IDENT { keyframes-blocks }`;
> `keyframes-blocks: [keyframe-selectors block] *`;
> `keyframe-selectors: [from to percentage] | [0% 50% 100%]`

其中IDENT是一个动画的名称，可以去一个任意定义的动画名称，percentage是一个百分比值，用来定义某个时间段的动画效果

例子：
```css
keyframes mymove {
	0% { CSS样式 }
	50% { CSS样式 }
	100% { CSS样式 }
}

keyframes mymove {
	from { CSS样式 }
	50% { CSS样式 }
	to { CSS样式 }
}
```

**注意**：相同的CSS样式可以用逗号隔开，最后处写上CSS样式

```css
keyframes mymove {
	0%, 60% { CSS样式 }
	50% { CSS样式 }
	100% { CSS样式 }
}
```

### 调用@keyframes声明的动画
keyframes只是用来声明一个动画，如果不通过别的CSS属性调用这个动画，是无任何动画效果的。我们可以再一个元素中通过animation属性来调用@keyframes声明的动画

**`注意`：**动画中设置的属性不会产生叠加效果，只是一次一次覆盖前一次出现的样式。就如CSS同一元素样式，最后出现的权限是最大的


### Animation子属性详解

#### animation-name

animation-name属性主要是用来调用动画（通过@keyframe声明的动画）
> 值：none | INDET（声明的动画名称）
> 初始值：none


#### animation-duration
animation-duration主要用来设置CSS3动画播放时间（一次@keyframes声明动画的执行时间）
> 值：time
> 初始值：0


#### animation-timing-function/animaiton-delay
animation-timing-function主要用来设置动画播放方式（和trasition的timing-function/delay一样）

#### animation-iteration-count
animation-iteration-count主要用来设置动画执行的次数
> 值：number | infinite（无限次的播放）
> 默认值：1

#### animation-direction
animation-direction设置动画在每次运行完后是反向运行还是重新回到开始位置重复运行
> 值：normal | alternate
> 默认值：normal


#### animation-play-state
animation-play-state规定动画正在运行还是暂停

> 值：running | pasued
>默认值： running

介绍：你可以在 JavaScript 中使用该属性，这样就能在播放过程中暂停动画。


#### animation-fill-mode
animation-fill-mode属性规定动画在播放之前或之后，其动画效果是否可见。

> animation-fill-mode : none | forwards | backwards | both;
> 默认：none
介绍：若该值为forwards，则表示动画完成后保留最后一个关键帧中的属性值，该值为backwards时则恰好相反，表示在动画延迟之前就使得元素应用第一个关键帧中的属性值，而该值为both时则表示同时包含forwards和backwards两种设置。在本例中，我们使用backward或both均可




### 性能

#### 关键渲染路径
动画性能高，从直观体验上是动画没有抖动和卡顿，从数字上是渲染达到了60fps。60pfs就是每秒60帧，所以每帧的时间只有1000ms / 60 = 16.67ms。但是实际上，浏览器在每一帧还要做一些额外的事情，所以如果要达成60fps，我们需要保证每一帧的时间在10ms到12ms。

#### 我们先来看看浏览器的每一帧渲染都做了哪些事情。

1. JavaScript
动画大多是由JavaScript触发的，比如改变位置、尺寸等等，现在大多数开发者使用CSS Animation，CSSTransition，这些动画只在开始的时候会执行JavaScript，动画过程中的每一帧都不会再有JavaScript的执行。但是CSS的动画接口是比较有限的，在现阶段和Native比还差很多，比较复杂的动画如果CSS不能完成，就需要使用requestAnimationFrame函数，这样每帧都会有JavaScript的计算。

2. Style
当一个新的样式应用到Dom上的时候，就会引起Style的计算，同JavaScript，如果开发者使用CSS Animation，CSS Transition，那么浏览器只有在动画开始之前会做Sytle的计算，而requireAnimationFrame会在每帧都计算。

3. Layout
当新的CSS样式触发了Layout，比如修改了width, height, position，这时浏览器需要重新Layout受到影响的元素，大部分情况下，即使一个位置很远的元素发生很小的宽度改变，也会引起整个document的Layout，这在动画里是一个性能非常低的实现，应该尽量避免。

4. Paint
Layout变化后，受到影响的元素会重新Paint，如果遇到首次加载图片，浏览器需要将图片先解码放入内存（Image Decode）。Painting是在多个Surface上进行的，最后会出来多个Layer。

5. Composite
最后一步Composite就是把已经Paint好的各个Layer合成到一起。浏览器会将每个层分成多个Tiles去Paint，但是这些作为H5开发者来说是不能够控制的，这些层和Tiles信息会被传到GPU，最终由GPU负责渲染并显示在屏幕上。

#### width
![Alt text](http://img002.qufenqi.com/products/82/0b/820b86cb4258444abd804c5357c00a46.png)


#### 使用trasform
![Alt text](http://img003.qufenqi.com/products/2f/d7/2fd72a89a676c3e07fca2d54891e8eb6.png)



### 一些会带来页面性能的属性
![Alt text](http://img003.qufenqi.com/products/87/5f/875f743760365d4deec57f9e6bd09756.png)

想知道更多，[请戳我](https://csstriggers.com/)


### 移动端用CSS开启硬件加速
1. 元素的3D变换
2. transform: translateZ(0)
3. 在 Chrome and Safari中，当我们使用CSS transforms 或者 animations时可能会有页面闪烁的效果

```css
{
   -webkit-backface-visibility: hidden;
   -moz-backface-visibility: hidden;
   -ms-backface-visibility: hidden;
   backface-visibility: hidden;
 
   -webkit-perspective: 1000;
   -moz-perspective: 1000;
   -ms-perspective: 1000;
   perspective: 1000;
}
```
4. transform: translate3d(0, 0, 0)

#### 原理：浏览器通过该样式创建了一个独立图层，图层中的动画则有GPU进行预处理并且触发了硬件加速。著作权归作者所有。


### 可以应用到项目的地方
1. 小的交互（上拉加载、点击按钮时显示loading、tab切换）
2. 单页面交互（如帮助中心）
3. 图片懒加载时图片显示效果微调

### 文档
1. [CSS animation和transition的性能探究](http://zencode.in/18.CSS-animation%E5%92%8Ctransition%E7%9A%84%E6%80%A7%E8%83%BD%E6%8E%A2%E7%A9%B6.html)
2. [H5动感影集性能分析](http://www.tqtan.com/2015/11/26/dynamic-album-performance-analysis/)
3. [30个CSSloading效果](http://simbyone.com/demo/30-css-page-preload-animations/)
4. [19中loading效果](http://wow.techbrood.com/fiddle/29490)
5. [硬件加速也有坑](http://div.io/topic/1348)
6. [避免前端页面卡顿](https://zhuanlan.zhihu.com/p/25166666?refer=dreawer)
7. [H5动画1](http://chuansong.me/n/1813682951719)
8. [H5动画2](http://chuansong.me/n/1818310351619)
9. [深入理解trasition](http://www.cnblogs.com/xiaohuochai/p/5347930.html)
10. [w3cAnimation](http://www.w3school.com.cn/cssref/pr_animation.asp)
11. [w3cTransition](http://www.w3school.com.cn/cssref/pr_transition.asp)
12. [CSS动画之硬件加速](https://www.w3cplus.com/css3/introduction-to-hardware-acceleration-css-animations.html`enter code here`)
13. [CSS animation和transition的性能探究](http://zencode.in/18.CSS-animation%E5%92%8Ctransition%E7%9A%84%E6%80%A7%E8%83%BD%E6%8E%A2%E7%A9%B6.html)
14. [渲染性能](https://developers.google.com/web/fundamentals/performance/rendering/)
15. [H5动画60fps之路](https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=206984354&idx=1&sn=493f4729da146fa22506e6ecb386291a&scene=21#wechat_redirect)
16. [使用Chrome DevTools的Timeline分析页面性能](https://segmentfault.com/a/1190000003991459)

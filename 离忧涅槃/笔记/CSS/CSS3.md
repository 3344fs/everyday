## 一、边框阴影

box-shadow

边框阴影

（X轴偏移，Y轴偏移，模糊半径，阴影半径，颜色，内阴影/外阴影）

例：

```css
box-shadow: 3px 3px 9px 3px #f00 inset;
```

## 二、相对于父元素的选择器

first-child	查找它父元素的第一个子元素，相对于当前元素的父元素，切类型和本元素相同有效

first-of-type	查找它父元素的第一个子元素，相对于当前元素的父元素，切类型和本元素相同有效

nth-child(数字/表达式)	例：nth-child(2n)

empty	元素中没有任何内容时被选中

## 三、锚点

```html
<a href="#a1">1</a>
<div id="a1"></div>
```

target	当目标被锚点选中时触发的样式

例：

```css
div:target{
    background-color: #f99;
}
```

## 四、伪元素

before	注意：添加content后才可以用

例：

```css
div:before{
    content: '';
    ...
}
```

after



## 五、文本阴影

font-shadow	X，Y，模糊度，颜色

div{
		font-size: 50px;
		text-shadow: 2px 2px 2px  #f99;
	}

## 六、怪异盒模型

```css
box-sizing: border-box;
```

## 七、圆角

```css
border-radius: 30px;
border-radius: 120px/60px;	//设置X，Y轴方向角度不同的圆角
border-radius: 10px 20px 30px 40px / 50px 60px 70px 80px;	//
```

## 八、渐变

1.线性渐变

linear-gradient(方向/左右，颜色 位置、颜色位置、颜色 位置)

例：

```css
background: linear-gradient(30deg,#009 0%,#f99 50%,#00f 100%) ;
```

2.径向渐变

radial-gradient(渐变状态是否跟随图形，坐标)

是否跟随形状变化：circle(不跟随，一直为正方形)，ellipse(跟随变化，默认)

大小：farthest-side(最近边)	closest-side(最远边)	farthest-corner(最近角)	closest-corner(最远角)	

例：

```css
background: radial-gradient(circle farthest-side at 10px 10px,#f00,#0f0);
```

3.重复渐变

repeating-radial-gradient()

例：

```css
repeating-radial-gradient(circle farthest-side at 30px 30px,#f00 0%,#00f 10%,#f00 10%,#00f 20%);
```

## 九、背景

background-attachment: 元素滚动时背景是否滚动	fixed(固定不动)	scroll(背景跟随元素滚动，但不跟随内容滚动)	local(滚动元素内容时滚动)

background-size:contain;

```css
background-image: url(img/3.jpg);

background-repeat: repeat;//no-repeat repeat-x repeat-y round(平铺元素背景,会缩放图片) space(平铺元素背景,会产生间距)

background-attachment: fixed;

background-size:contain;	//使图片等比例拉伸到最大，但不超出元素

background-size: cover;		//使图片等比例拉伸到填满整个背景，会超出元素

background-origin: content-box;	//设置背景图从哪块开始填充，content-box(从内容开始填充)	padding-box(从padding开始填充)	border-box(从border开始填充)

background-clip: border-box;	//设置内容裁切，content-box(显示content及里边的内容)	padding-box(显示padding及内部内容)	border-box(显示border及以内的内容)
```

## 十、过渡

```css
transition-property: all;	//选择过渡类型
transition-duration: 2s;	//过渡时间
transition-timing-function: ease;	//过渡时间变化
transition-delay: 1s;	//延时时间

transition: all 2s ease 1s;		//简写
```
## 十一、transform

```css
transform: translate(10px,10px);	//根据当前元素改变位置
transform: scale(1，1);	//缩放
transform: rotate(30deg);	//旋转
transform: skew(30deg,-30deg);	//斜切
transform-origin: 0 0;	//设置中心点
transform: translate3D(0,0,10px);	//3D移动
transform: scale(1，1，1);	//3D缩放
transform: rotate3D(1,0,0,90deg);	//3D旋转
transform: rotate3DX(90deg);	//3D旋转
transform-style: preserve-3d;	//设置保留3D变换后的样式
perspective: 200px;		//设置观察距离（默认在0，0，0）
perspective-origin: 0px 0px;	//设置观察角度
```

例：

3D盒子

```html
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<meta http-equiv="X-UA-Compatible" content="ie=edge" />
	<title>Document</title>
</head>
<body>
	<div id="box3d">
		<div class="top">上</div>
		<div class="bottom">下</div>
		<div class="left">左</div>
		<div class="right">右</div>
		<div class="qian">前</div>
		<div class="hou">后</div>
	</div>
</body>
<style type="text/css">
	#box3d{
		position: relative;
		margin: 200px auto;
		width: 200px;
		height: 10px;;
		top: 0;
		left: 0;
		transform: rotate3D(2,2,1,30deg);
		transform-style: preserve-3d;
		perspective: 200px;
		perspective-origin: 0px 0px;
	}
	#box3d div{
		width: 200px;
		height: 200px;
		position: absolute;
		top: 0;
		left: 0;
		opacity: .5;
	}
	.top{
		background-color: #f00;
		transform: translateY(-100px) rotateX(90deg);
	}
	.bottom{
		background-color: #0f0;
		transform: translateY(100px) rotateX(90deg);
	}
	.left{
		background-color: #00f;
		transform: translateX(-100px) rotateY(90deg);
	}
	.right{
		background-color: #f99;
		transform: translateX(100px) rotateY(90deg);
	}
	.qian{
		background-color: #999;
		transform: translateZ(100px);
	}
	.hou{
		background-color: #99f;
		transform: translateZ(-100px);
	}
</style>
</html>
```

## 十二、动画

```css
/*动画名*/
animation-name: fei;
/*执行时间*/
animation-duration: 1s;
/*循环次数*/
animation-iteration-count: infinite;
/*来回交替*/
animation-direction: alternate;
/*延迟时间*/
animation-delay: .5s;
/*结束后保留结束样式*/
animation-fill-mode: forwards;
/*动画执行时间函数*/
animation-timing-function: linear;
/*是否播放动画,paused 暂停,running 播放*/
animation-play-state: running;
```

## 十三、多列布局

```css
/*設置多列佈局*/
column-count: 4;
/*添加分界线*/
column-rule: 1px solid #f00;
/*添加间距*/
column-gap: 50px;
/*设置列宽*/
column-width: 500px;
/*设置跨列,all表示占一行*/
column-span: all;
```
## 十四、弹性盒子

参考网站：https://www.cnblogs.com/MrSaver/p/9002074.html

添加给父元素的

```css
display: flex;
设置元素为弹性盒子

justify-content: space-around;
/*子元素排列方式
flex-start：从左开始，
flex-end：从右开始，
center：中间，
space-between：左右无缝隙的平均分布，
space-around：平均分布在元素左右*/

flex-wrap: wrap;
/*是否换行,
wrap：换行，
nowrap：不换行，
wrap-reverse：下方开支排列*/

flex-direction: row-reverse;
/*主轴方向
row：水平，
colum：竖直 ，
row-reverse：水平翻转顺序，
column-reverse：数值翻转顺序*/

flex-flow: nowrap row-reverse; 
/*flex-wrap 和 flex-direction 的结合*/

align-items: stretch;
/*设置次轴方向的对齐方式，
flex-start：从上开始，
center：居中，
flex-end：从下开始，
baseline：项目第一行文字的基线对齐，
stretch：次轴拉伸填满父级元素*/

```

添加给子元素的

```css
flex-grow: 1;
/*父元素留白区域填充到子元素中 ，按照份数计算，默认0*/

flex-shrink: 0;
/*父元素太小时子元素收缩度，默认1，0 时不缩小*/

flex: 1;
/*设置每个子元素占父元素的几份*/

align-self: center;
/*设置子元素的次轴对其方式*/

```

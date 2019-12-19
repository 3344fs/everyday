## 一、表单新属性

### 1.form 表单新属性

#### a.type值

例：

```html
<input type="email" />
```

email：e-mail格式（可添加 multiple 后填写多个邮箱，用逗号分隔）

tel：不验证电话，在移动端可打开数字键盘，限制只能输入数字

url：连接地址（网址或文件路径）

date：日期选择框（年月日）

month：月份选择框（年月）

time：时间选择框

week：星期选择框（年，周）

datetime-local：时间日期选择

number：数字输入框（只可输入数字，有上限值 max，下限值 min，初始值 value）

range：滑动条（有上限值 max，下限值 min，初始值 value）

search：搜索框（可点击右边“X”清除框内文字）

color：颜色选择器

file：文件上传（可添加 multiple 后选择多个文件）

submi：提交（自验证表单中内容格式是否正确）

form：在form外的 input 可与其他表单关联提交（关联表单提交时也会将此 input 的值一起提交）

例：

```html
<form action="" id="tijao">
    <input type="email" name="" id="" value="" />
    <input type="submit" name="" id="" value="提交" />
</form>
<input type="email" form="tijiao"/>
```

#### b.placeholder 文本占位

#### c.autofocus 自动获取焦点

#### d.autocomplete 输入提示

两个条件：1.必须提交成功，2.必须要有 name 属性

#### e.required 必填项

#### f.pattern 正则验证

### 2.form表单新事件

oninput	#表单内容发生改变时触发

例：

```html
<form action="" method="post">
    <input type="text" name="inputtext" id="inputtext" value="" />
    <input type="submit" value=""/>
</form>
<script type="text/javascript">
	document.getElementById("inputtext").oninput = function(){
		console.log(this.value)
	}
</script>
```

onkeyup	#键盘弹起时出发

oninvalid	#验证失败时触发（可修改提示内容）

例：

```html
<form action="">
    <!--<input type="text" name="inputtext" id="inputtext" value="" /><br />-->
    <input type="email" name="11" id="email" value="" /><br />
    <input type="submit" value="tijiao" id="1111"/><br />
</form>
<script type="text/javascript">
	document.getElementById("email").oninvalid = function(){
		console.log("提交失败")
		this.setCustomValidity('提示内容')
	}
</script>
```

onchange	#事件会在域的内容改变并失去焦点时触发

比如：在选择文件后执行

### 3.进度条

#### progress

默认左右晃动，可设置大小来固定

属性：

max：（最大值）

value：（当前值）

例：

```html
<progress max="100" value="50"></progress>
```



#### meter

默认为 0，但 value 小于较小值或大于较大值时变色提醒

属性：

max：最大值

min：最小值

high：规定的较大值

low：规定的较小值

value：当前值

例：

```html
<meter max="100" min="0" low="30" high="80" value="88"></meter>
```



## 二、音频视频处理

原生接口（ JQuery 要转为原生 JS ）：

load()	重新加载

play()	开始

pause()	暂停

currentTime()	当前播放时间

duration()	总时长

paused()	视频播放状态

事件：

canplay()	当音频/视频可以播放时触发

pause()	音频/视频暂停时触发

play()	音频/视频开始播放时执行

ended()	播放完毕时触发

timeupdate当前播放位置改变时

例：

```js
var video = $("#video")[0]
video.play()
```



### 1.音频

audio

属性：

*src：文件路径

*controls：添加控制器（必填）

autopaly：自动播放

loop：循环

例：

```html
<audio src="mp3/求佛-群星.mp3" controls="1"></audio>
```

### 2.视频

video

属性：

width：宽度（宽度或高度设置一个就行，让其等比缩放）

height：高度（宽度或高度设置一个就行，让其等比缩放）

poster：当视屏还没有完全下载或	用户还未点击前的默认封面，默认显示第一画面

autoplay：自动播放

loop：循环

source：准备多个格式的文件让浏览器自动选择支持的那个

例：

```html
<video width="800px" height="" controls="1" poster="mp4/test.jpg" autoplay loop>
    <source src="MP4/录像.mp4" type="video/mp4"></source>
    <source src="MP4/录像.mp4" type="video/ogg"></source>
    <source src="MP4/录像.mp4" type="video/webm"></source>
    当前浏览器不支持 video直接播放，点击这里下载视频： <a href="myvideo.webm">下载视频</a>
</video>
```



## 三、Canvas

### 线：

```js
//帽子
ctx.lineCap = 'round';
//拐点
ctx.lineJoin = 'round'
//设置虚线
ctx.setLineDash([5])
//获取虚线排列方式（数组）
ctx.getLineDash()
//线条偏移（负值往右偏移）
ctx.lineDashOffset = -70
```



### 设置大小在元素本身设置

例：

```html
<canvas width="500" height="300"></canvas>
```

两条不同颜色和宽度的平行线

```js
<script type="text/javascript">
	window.onload = function () {
//		获取画布
		var myCanvas = document.querySelector('canvas')
//		获取绘制工具
		var ctx = myCanvas.getContext('2d')
		
		
//		开启新路径
		ctx.beginPath()
//		移动画笔
		ctx.moveTo(100,100)
		ctx.lineTo(200,100)
//		颜色
		ctx.strokeStyle = '#f00'
//		宽度
		ctx.lineWidth = 10
//		描边
		ctx.stroke()
		
		ctx.beginPath()
		ctx.moveTo(100,200)
		ctx.lineTo(200,200)
		ctx.strokeStyle = '#0f0'
		ctx.lineWidth = 5
		ctx.stroke()
	}
</script>
```

### 填充的三角形

```js
<script type="text/javascript">
	window.onload = function () {
		var myCanvas = document.querySelector('canvas')
		var ctx = myCanvas.getContext('2d')
		
		ctx.moveTo(100,100)
		ctx.lineTo(200,100)
		ctx.lineTo(200,200)
		ctx.lineTo(100,100)
//		填充
		ctx.fill()
	}
</script>
```

### 自动闭合

```
		var myCanvas = document.querySelector('canvas')
		var ctx = myCanvas.getContext('2d')
		
		ctx.moveTo(100,100)
		ctx.lineTo(200,100)
		ctx.lineTo(200,200)
//		自动闭合
		ctx.closePath()
//		填充
		ctx.fill()
```

### 非零填充

例：（镂空的正方形，检测是否和填充的图片方形相同，相同则填充，不同则不填充）

```js
var myCanvas = document.querySelector('canvas')
var ctx = myCanvas.getContext('2d')

ctx.moveTo(100,100)
ctx.lineTo(300,100)
ctx.lineTo(300,300)
ctx.lineTo(100,300)
ctx.closePath()

ctx.moveTo(150,150)
ctx.lineTo(150,250)
ctx.lineTo(250,250)
ctx.lineTo(250,150)
ctx.closePath()

ctx.moveTo(170,170)
ctx.lineTo(230,170)
ctx.lineTo(230,230)
ctx.lineTo(170,230)
ctx.closePath()

//		填充颜色
ctx.fillStyle = 'red'
ctx.fill()
```

### 圆弧

```js
//画一个 canvas 中心,半径150,顺时针的 1/4 的圆弧
var w = ctx.canvas.width
var h = ctx.canvas.height
ctx.arc(w/2,h/2,150,0,Math.PI/2,false)
ctx.stroke()
```

### 扇形

```js
var w = ctx.canvas.width
var h = ctx.canvas.height
ctx.moveTo(w/2,h/2)
ctx.arc(w/2,h/2,150,0,Math.PI/2,false)
ctx.closePath()
ctx.stroke()
```



## 四、SVG

可缩放矢量图（使用XML格式定义图形，放大不失真）

## 五、拖放API

draggable=‘true’	使得元素可以拖拽，图片和超链接默认可以拖放,天界给document就可以实现全局拖拽

### 1.拖拽元素

**ondrag**	拖拽过程中执行（持续的）

**ondragstart**	开始拖拽时执行

**ondragleave**	鼠标离开拖拽元素时执行

**ondragend**	结束拖拽时执行

### 2.目标元素

**ondragenter**	当拖拽元素进入时（持续的）

**ondragover**	停留在目标元素上时（持续的）

**ondrop**	在目标元素中松开鼠标时（默认不被触发，需要在 ondragover 中阻止默认行为，在参数 e 中添加 e.preventDefault() ）

**ondragleave**	鼠标离开时目标元素

## 六、Web存储

### 1.cookie

特征：

1. 不同的浏览器存放的cookie位置不一样，也是不能通用的。
2. cookie的存储是以域名形式进行区分的，不同的域下存储的cookie是独立的。
3. 我们可以设置cookie生效的域（当前设置cookie所在域的子域），也就是说，我们能够操作的cookie是当前域以及当前域下的所有子域
4. 一个域名下存放的cookie的个数是有限制的，不同的浏览器存放的个数不一样,一般为20个。
5. 每个cookie存放的内容大小也是有限制的，不同的浏览器存放大小不一样，一般为4KB。
6. cookie也可以设置过期的时间，默认是会话结束的时候，当时间到期自动销毁

### 2.localStorage

​		大小 5M 左右

​		存储在当前页面的内存中

​		页面关闭就消失

#### 	a.存储

​		setItem(key,value)

​		例：	

```js
window.sessionStorage.setItem('key','value')
```

#### 	b.获取

​		getItem(key)

#### 	c.删除数据

​		removeItem(key)

#### 	d.清空数据

​		clear()

### 3.sessionStorage

​		内容大小：20M 左右

​		不同浏览器不可共享数据

​		永久生效，不会自动清楚

#### 	a.存储

​		setItem(key,value)

​		例：

```js
window.localStorage.setItem('key','value')
```

#### 	b.获取

​		getItem(key)

#### 	c.删除数据

​		removeItem(key)

#### 	d.清空数据

​		clear()

### 4.缓存

第一步	在html标签中添加 manifest

例：

```html
<html lang="zh" manifest="fs.appcache">
</html>
```

第二部	添加fs.appcache 内容

fs.appcache 文件内容：

```html
CACHE MANIFEST
#上邊的必須是第一行

#需要緩存的內容
CACHE:
../img/1.jpg

#每次打開重新獲取的內容
NETWORK

#如果文件找不到，用拎一個代替
FALLBACK
../img/1.jpg ../img/2.jpg
```



## 七、Web Workes

## 八、Web Sockets

## 九、百度地图

#### 获取地理位置

  navigator.geolocation

## 十、服务器发送事件

## 十一、语义化标签

### 1.标签

1）.header：头部

2）.nav：导航

3）.main：文章内容

4）.article：文章

5）.aside：主题内容之外

6）.footer：底部

例：

```html
<header>头部</header>
<nav>导航</nav>
<main>
	<article>主要内容</article>
	<aside>其他内容</aside>
</main>
<footer>底部</footer>
```
### 2.兼容处理

ie8及以下版本不兼容，处理办法：

第一种：

创建标签，例：

```js
document.createElement("header")
```

第二种：

引入第三方插件，例：

```js
<script src="html5shiv.min.js"></script>
```

## 十二、操作dom元素

### 1.获取

#### querySelector

选择符合条件的第一个元素（可传入类名，id，以及标签名）

例：

```js
li = document.querySelector('li')
li = document.querySelector('.li')
li = document.querySelector('#li')
```

#### querySelectorAll

返回符合条件的所有元素的数组

### 2.操作

#### classList

返回当前选中元素的所有类名组成的列表

例：

```html
<ul>
    <li class="11 22">111</li>
    <li>222</li>
    <li>333</li>
</ul>

<script type="text/javascript">
    var li = document.querySelector('li')	//选择 li 中的第一个
    console.log(li.classList)	//输出数组[11,22]
</script>
```

#### add	添加样式

例：

```js
var li = document.querySelector('li')
li.classList.add('a')
```

#### remove	移除样式，元素还在

#### toggle	切换

#### contains	判断是否包含该样式

## 十三、网络及接口

### 1.网络监听接口

网络接通事件：ononline

例：

```js
window.addEventListener('online',function(){
    alert("网络接通")
})
```

网络断开事件：onoffline

### 2.全屏接口

#### 全屏：requestFullScreen()

给元素添加，

例：

```js
var test = document.getElementById("imgbox")
document.getElementById("quan").onclick = function() {
    if(test.requestFullScreen) {
        test.requestFullScreen()
    } else if(test.webkitRequestFullScreen) {
        test.webkitRequestFullScreen()
    } else if(test.mozRequestFullScreen) {
        test.mozRequestFullScreen()
    } else if(test.msRequestFullScreen) {
        test.msRequestFullScreen()
    } else if(test.oRequestFullScreen) {
        test.oRequestFullScreen()
    } else {
        alert("全屏失败")
    }
}
```

#### 退出全屏：cancelFullScreen()

给整个文档（document）添加

例：

```js
document.getElementById("exit").onclick = function() {
    if(document.cancelFullScreen) {
        document.cancelFullScreen()
    } else if(document.webkitCancelFullScreen) {
        document.webkitCancelFullScreen()
    } else if(document.mozCancelFullScreen) {
        document.mozCancelFullScreen()
    } else if(document.msCancelFullScreen) {
        document.msCancelFullScreen()
    } else if(document.oCancelFullScreen) {
        document.oCancelFullScreen()
    } else {
        alert("退出全屏失败")
    }
}
```

#### 是否全屏：fullscreenElement

给整个文档（document）添加

例：

```js
document.getElementById("shifou").onclick = function() {
    if(document.fullscreenElement || document.webkitFullscreenElement || document.mozFullscreenElement || document.msFullscreenElement || document.oFullscreenElement){
        console.log('全屏')
    }else {
        console.log('非全屏')
    }
}
```



## 十四、浏览器兼容

### 1.浏览器前缀

chrome：webkit

Firefox：moz

ie：ms

opera：o

## 十五、Filereader读取文件

### 1.readAsText（）

读文本文件，返回字符串，默认UTF-8

### 2.readAsBinaryString（）

读取任意类型的文件，返回二进制字符串，一般读取数据传给后台，	

### 3.readAsDataURL（）

读取文件，获取一段以 data 开头的字符串，这段字符串就是dataurl，dataurl一般指图像或可嵌入到文档了文件格式，如：base64 格式文件。

```
1.创建文件读取对象
2.读取文件，获取DataURL
3.获取数据（注意获取数据时间，要在读取结束再获取，否则获取不到，所以用到读取监听事件）
```



```html
<body>
    <form action="" >
        <input type="file" name="" id="file" value="" onchange="readfile()" /><br />
        <img src=""/>
        <input type="submit" value="提交"/>
    </form>
</body>
<script type="text/javascript">
        function readfile() {
            var file = document.getElementById("file").files	//w獲取元素的files值（元素中所有文件組成的列表）
            var read = new FileReader();	//創建文件讀取對象
            read.readAsDataURL(file[0]) //1.沒有返回值，需要參數（可以嵌入到文檔的文件），將讀取結果存儲到對象的result中
            read.onloadend = function(){	//监听读取状态
                document.getElementsByTagName('img')[0].src = read.result	//将读取到的数据传给 img
            }
        }
</script>
```

文件读取监听（添加给对象）：

onabort：读取文件终端时触发

onerror：读取文件错误时触发

onload：读取文件成功时触发

onloadend：读取文件完成时触发，无论成功与否

onloadstart：开始读取问价时触发

onprogress：读取文件过程中持续触发

### 4.abort（）

终端读取

## 十六、解决onmousemove的闪烁问题

在闪烁元素上的 css 中加	pointer-events: none;
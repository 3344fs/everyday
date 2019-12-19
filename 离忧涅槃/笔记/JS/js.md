## 发展历史了解

97年以前是没有标准

1997 年开始  ECMAScript ESI

1998年指定了  ES2 的一个标准，在 ESI 的基础増加了一些功能

1999年制定了  ES3 的一个标准，在 ES2的基础上増加了一些方法（基本被所有浏览器）

2000 年提案 ES4的一个标准，基本上是把前面的推翻，从新给你一套标准（搁置，直至）

2009年制定了  ES5 (ES3.1) , 是 在 ES 3的基础上増加了一些内容

2011年指定了  ESS.1版本，是在 ES3.1的基础上增加了一些内容

2012年的时候，基本上各大浏览器都己经可以支持 ESS.1的语法

2015年敲定 ES6就是在 ESS.1的基础上，增加了  ES4 的 内容

各大浏览器对 ES6的兼容都不是很好

出现了一个 babeL , 他 可 以 把 ES6的语法转换回 ES5的语法格式

2015年规则的制定者，起名这个事情不规范，所以从15 年以后，全部以年份命名

ES6  就是  ES 20150

2016 制 定 了  ES2016行业内部叫做 ES7，在 ES6的基础上增加

2017指定了  ES2017行业内部叫做 ES8,在 ES7的基础上增加

2018 指 定 了  ES2018行业内部叫做 ES9,在 ESS 的基础上增加

2019 指 定 了  ES2019行业内部叫做 ES10,在 ES9的基础上増加

## 严格模式

开启严格模式：在作用域开始加上 `"use strict"`

+ 变量必须写 var

+ 函数的形参不能重名

+ 全局函数没有 this

+ ......

  



## 输出

+ 控制台输出

console.log()	输出值

console.dir()	输出对象的详细值

console.table	把JSON对象按照表格的形式输出

+ 浏览器窗口弹窗

alert

confirm

prompt

+ 页面中输出

document.write



## 变量

+ 定义方式
  + var
  + let
  + const
  + function
  + import
  + class
  + ....



## 数据类型

+ 基本数据类型
  + 数字 number（包含 NaN）
    + NaN 不是一个数但属于数字类型 ( NaN 不等于 NaN)
  + 字符串 string
  + 布尔 boolean
  + 空对象指针 null
  + 未定义 undefined
+ 引用数据类型
  + 对象数据类型
    + {} 普通对象
    + [] 数组对象
    + 正则表达式
    + Math数学函数对象
    + 日期对象
    + ...
  + 函数数据类型 function



## 函数

### 函数的底层运行原理

1.建函数

```js
function fn(n,m){
	var res = n + m;
	return res
}
```

2.执行函数

```
var AA  = fn(10,20)
console.log(aa)
```

### 函数类型





## 系统方法

+ 事件信息
  
  window.event
  
+ 普通方法
  
  + Typeof()	返回内容的数据类型
  + toString()    将内容转为字符串类型（例：a.toString() ，null 和 undefined 禁止使用）
  
+ 数组
  + Number()	将内容转为数字
  + parseInt()/parseFloat( [val] , [进制] )     从左到右查找有效数字，知道出现非有效数字后停止

+ 字符串
  
  + ​	

## 操作类名

1. 添加

   ```js
   test.classList.add("a")
   ```

2. 删除

   ```js
   test.classList.remove("test")
   ```

3. 替换

   ```js
   test.classList.replace("a","b")
   ```

4. 切换

   ```
   test.classList.toggle("a")
   ```

   

## ajax

+ ajax请求步骤

1. 创建一个实例化对象

   ```js
   var xmlHttp = new XMLHttpRequest()
   ```

2. 配置请求方式和请求地址

   + get / post
   + 请求路径
   + 同步异步（true 异步可省略，false 同步）

   ```js
   xmlHttp.open('GET','http://localhost/php/log.php?test=12')
   ```

3. 发送请求（.send() 方法，如果是 post 请求，需要将传递是数据在 send 中带入）

   ```js
   xmlHttp.send()
   xmlhttp.send('test=post')
   ```

4. 接受结果
   注意：

   ​	获取状态码时需要考虑同步异步，如果是异步，则将先获取状态码再返回结果。
   解决办法：1.将请求变为同步（不建议），2.当状态码改变为 4 时执行

   ```js
   xmlHttp.response //接收到的结果
   ```

   

```js
//创建 ajax 对象
	var xmlHttp = new XMLHttpRequest()
//连接服务器
	xmlHttp.open('GET','http://localhost/php/log.php?test=12')
//post请求需要设置请求头
	//xmlHttp.setRequestHeader("Content-Type","application/x-www-form-urlencoded")
//发送请求,post 需要将参数传递到 send函数中
	xmlHttp.send()
//接收结果，状态码变动执行函数
	xmlHttp.onreadystatechange = function (){
		//	判断状态码
		if(xmlHttp.readyState === 4 && 200 <= xmlHttp.status <= 299){
			//输出接收到的数据
			console.log(xmlHttp.response)
		}
	}
//第二种接受结果方法，自动判断判断状态码和接受成功时执行（不兼容 ie 6,7,8）
    xmlHttp.onload = function (){
        console.log(xmlHttp.response)
    }
```

+ ajax状态码
  1. 0=>实例化成功
  2. 1=>表示配置请求地址和请求方式成功
  3. 2=>请求已经发送出去
  4. 3=>相应已经回到浏览器，正在解析
  5. 4=>相应已经解析完毕，可以再客户端正常使用



## 跨域

+ 同源组策略

  所谓同源是指，域名，协议，端口相同。

  同源策略是浏览器的行为，是为了保护本地数据不被JavaScript代码获取回来的数据污染，因此拦截的是客户端发出的请求回来的数据接收，即请求发送了，服务器响应了，但是无法被浏览器接收。

+ 跨域解决方案

  1. jsonp（辉煌在5年前，现在市场上很少使用）

     scipt内容：

     ```js
      //1.创建一个 script标签
     const script = document.createElement('script')
     script.className = 'jsonp'
     script.src = 'http://127.0.0.1:80/php/jsonp.php?callbacke=fn'
      
     //先准备号一个函数
     function fn (res){
         console.log(res)
         //已经拿到数据了,该进行页面渲染了script标签就没有用
         document.body.removeChild(script)
     }
     //插入script 标签
     document.body.appendChild(script)
     ```
  
     php内容
  
     ```php
     <?php
         header('content-type:text/html;charset=utf-8;');
     	$callbacke = $_GET["callbacke"];
         echo $callbacke . '({name:"方式",age:18,sex:"男"})';
     ?>
     ```
  
  2. cors 跨域资源共享（市场上普遍使用）
  
     这个是后端在服务器上添加代码，让服务器告诉浏览器我允许请求资源（放在php的头部）
  
     ```php
     //跨域
     header("Access-Control-Allow-Credentials: true");
     header("Access-Control-Allow-Origin: *");
     //CORS
     header("Access-Control-Request-Methods:GET, POST, PUT, DELETE, OPTIONS");
     header('Access-Control-Allow-Headers:x-requested-with,content-type,test-token,test-sessid');
     ```
  
  3. 反向代理（市场上普遍使用）
  
     服务器用 Nginx ，在 Nginx 服务器上的配置文件中添加代理的配置

## http请求

+ 链接步骤

1.  建立链接
    基于TCP/IP协议的三次握手

2. 发送请求
    以一个请求报文的形式发送给服务端

3. 接受响应
    以一个响应报文的形式发送给客户端

4. 断开链接
    基于TCP/IP协议的四次挥手

  

+ 一个请求报文都包含哪些内容

  1. 请求行

     GET /index.htmL HTTP/1.1

     GET请求方式

     /index.htmL 请求 URL + HTTP/1.1请求的协议版本

  2. 请求头

     HOST： 请求的主机（从哪个地址发送的请求)

     User-Agent:请求的浏览器版本

     Accept:我希望你给我返回一个什么数据格式

     COOKIE：每一个请求报文里面都会由（现在不聊)

     content-type；表示我给你发送的数据时什么格式

     Date:	请求时间

     ...... 

  3. 请求空行 

     —个空行

     分割请求头和请求体

  4. 请求体

     就是客户端要给服务端的信息

+ 请求方式

  常见的请求方式（get 和 post 为重点，其他了解）

  + HTTP/1.Q协议版本里面就有的

      1. GET通常用来表示我向服务器索要一些信息

      2. POST通常用来表示我想服务器发送一些信息

      3. PUT通常用来表示我向服务器发送=查需要修改或者添加的信息I

      4. DELETE通常用来向服务器发送一个消息，表示要删除某个数据

  + HTTP/1.1协议版本才有的

    5. HEAD向服务端索要一些数据，但是不是为了要数据只是为了要一个响应头信息

    6. CONNECT表示管道链接转换为代理链接模式

    7. OPTION表示为了获取一些服务端信息

    8. PATCH向服务端发送一些消息用于修改数据（修改一部分数据使用)

+ GET 和 POST 请求的区别
  + GET
    + 请求参数直接拼接再地址栏（明文发送)
    + 有大小限制 （IE 2 M 左右 ，FF 2 QM 左右 ，Chrome 8 M 左右)
    + 相对不安全
    + 多用于向服务端请求数据
    + 发送的数据格式有限制（只接受 ASCII 码)
    + 会被浏览器自主缓存
  + POST
    + 请求参数写在请求体内的（暗文发送)
    + 理论上没有大小限制（服务器可以对他进行限制)
    + 相对安全
    + 多用于向服务端发送一些数据
    + 理论上对于数据格式没有限制（要和请求头里面的 content-type — 致)
    + 不会被浏览器自主缓存（可以设置）

​	

## 本地存储

+ Cookies

  默认会话结束过期，可以设置过期时间（前后端都可以改）

  ```js
  document.cookie	//获取
  document.cookie	= 'test'//设置
  
  //给 cookie 设置过期时间
  var time = new Date()//获取时间
  time.setTime(time.getTime() + 1000) //设置时间戳
  document.cookie = 'a = 10;expires = ' + time
  ```

+ Local Storage

  永久保存（只有前端可以更改）

  1. 设置（setItem）

     注意：对象或者数组需要转换成 json 格式。

     ```js
     var a = {
         name:"测试",
         age:18
     }
     localStorage.setItem("a",JSON.stringify(a))
     ```

  2. 获取（getItem）

     注意：对象或者数组需要 json 解析。

     ```js
     JSON.parse(localStorage.getItem("a"))
     ```

  3. 删除（removeItem / clear）

     ```js
     localStorage.removeItem("a")//删除单个
     localStorage.clear()//删除所有
     ```

     

+ Session Storage



## 异常

```
try{
	代码语句
}catch(err){
	处理语句
}
```



## 递归

需要一个出口：可以让函数终止的 return

```js
function jc(n) {	//计算 N 的阶乘
    if(n == 1){
        return 1;
    }
    return n * jc(n - 1);
}
var jc = jc(10)
console.log(jc)
```



## 闭包

+ 函数将拎一个函数 return 出去，返回的函数可调用原函数的变量

  例：

  ```js
  function fn () {
      var a = 2;
      function fn1 () {
          a++;
          console.log(a)
      }
      return fn1
  }
  var res = fn();
  res();
  res();
  ```

+ 缺点：

  原有的作用域链不会被释放，导致内存泄漏。

+ 优点：

  可实现累加，可进行存储



## 预编译

1.创建AO对象

2.找形参和变量声明，将变量和形参作为AO的属性名，值为 undefined

3.将实参值和形参值统一

4.在函数体里面找函数声明，值赋予函数体



## 立即执行函数

```js
(function a () {
    document.write(2)
}())
```



## 构造函数

注意：一般首字母大写，函数内不能写 return ，需要和 new 连用使 this 指向对象，当要给对象添加属性时写在构造函数体内，当需要给对象添加方法时卸载构造函数的 prototype 上，函数的 prototype 的 this 指向调用他的对象。

注意：但要给对象添加属性时写在构造函数体内，当需要给对象添加方法时卸载构造函数的 prototype 上。

```js
function People (name,age) {
    this.name = name;
    this.age = age;
}
var p1 = new People("fs",18)
console.log(p1)
```

## 内置构造函数

+ Set（像数组的集合，内容不重复，会自动把重复内容删除）

  1. size（数组长度）

     ```js
     var set = new Set([1,2,3,4,5])
     console.log(set)
     ```

  2. add（添加）

     ```js
     set.add(a)
     ```

  3. delete（删除，如果是复杂数据类型，直接删除没用，需要删除对应的地址）

     ```js
     set.delete(4)
     ```

  4. clear（清空）

     ```js
     set.clear(4)
     ```

  5. has（判断是否有该数据，返回 true / false ，判断的是 ===）

     ```js
     set.has(4)
     ```

  6. forEach（遍历数据集合）

     ```js
     var set = new Set([1,3,5])
     set.forEach(function (item,index,arr) {
         console.log(item)
     })
     //item 每一项
     //index 每一项
     //arr 原始 Set 集合
     ```

+ Map（像对象的数据集合，）

  1. set（设置成员）

     ```js
     var map = new Map()
     map.set(1,2)
     map.set({name:"黑"},{age:18})
     ```

  2. get（获取成员）

     ```JS
     console.log(map.get(1))
     ```

  3. delete（删除）

     ```js
     map.delete(1)
     ```

  4. clear（清空）

     ```js
     map.clear(1)
     ```

  5. forEach（遍历）

     ```
     map.forEach(function (item,index,arr) {
         console.log(item)
     })
     //item 每一项的 value
     //index 每一项的 key
     //arr 原始 Map 集合
     ```

  6. has（判断有没有）

     ```
     map.has(1)
     ```

  7. size（键值对数量）

## 原型

+ 实体

  __ proto __   => 原型	

  constructor => 构造函数

+ 构造函数

  prototype  => 原型

+ 原型



## 继承

和构造函数相关的使用方式，让 A 构造函数使用 B 构造函数的属性或方法

1. 原型继承

   

2. 借用构造函数继承

   

3. 组合继承

   

4. ES6 的继承

   extends , super

   注意

   ```js
   class Person {
       constructor (name){
       	this.name = name;
       }
   
       sayhi () {
       	console.log("你好")
       }
   }
   
   //需要用 extends 加 类名 来确定父类
   class Student extends Person {
       //需要接收父类的参数
       constructor (age,name){
       //要先执行 super() 再定义自己的变量
           super(name);
           this.age = age;
       }
   
       sayage (){
       	console.log("student")
       }
   }
   
   var item = new Student("12","as")
   console.log(item)
   ```

   



## arguments

类数组集合，存储着所有函数执行时，传递的实参信息（内置的，不论是否设置，都存在）

```
function fn () {
    console.log(arguments)
}
fn(1,2,3)
```



## 命名空间

可利用闭包将变量封装起来，这样就不污染全局变量

```js
var aa = (function () {
    var name = 'abc';
    function callname () {
        console.log(name);
    }
    return function () {
        callname()
    };
}())
aa();
```


## 连续调用

用 return this 实现函数的连续调用

```js
var aa = {
    a:function a () {
        console.log('a')
        return this;
    },
    b:function b () {
        console.log('b')
        return this;
    },
    c:function c () {
        console.log('c')
        return this;
    },
}
aa.a().b().c()
```



## 属性拼接

利用 对象的 [ ] 实现属性的拼接，aa.aa1 和 aa[ 'aa1' ] 一样

```js
var aa = {
    aa1:'a',
    aa2:'b',
    aa3:'c',
    co:function (num) {
        return this['aa' + num]
    }
}
console.log(aa.co(2))
```



## 数据类型检测

typeof [ ]	：用来检测数据类型

```
console.log(typeof "1");
let a = [];
console.log(typeof a);
```

instanceof	：用来检测当前实例是否属于某个类型



constructor	：基于构造函数检测数据类型



Object.prototype.toString.call( )	：检测数据类型最好的办法



## 事件对象

event

```
window.event	//以前只有 IE 有
function (e){
	console.log(e)	//事件的对象
}
```



## 浏览器默认事件

取消默认行为

e.preventDefault()	

return false

+ 自定义右击事件

  ```js
  <style type="text/css">
  	*{margin: 0; padding: 0;}
  	ul{
  		overflow: hidden;
  		width:100px;
  		border: 1px solid #ddd;
  		position: fixed;
  		top: 0;
  		left: 0;
  		cursor: pointer;
  	}
  	li{
  		list-style: none;
  		border-bottom: 1px solid #f99;
  		text-indent: 1em;
  	}
  	li:hover{
  		background-color: #d99;
  	}
  </style>
  <body>
  	<ul>
  		<li>1</li>
  		<li>2</li>
  		<li>3</li>
  		<li>4</li>
  		<li>5</li>
  	</ul>
  </body>
  <script type="text/javascript">
  	var ul = document.querySelector("ul")
  	var lis = document.querySelectorAll("li")
  	window.addEventListener('contextmenu',function (e) {
  		e.preventDefault()
  		var x = e.clientX;
  		var y = e.clientY;
  		ul.style.display = "block"
  		ul.style.top = y + "px"
  		ul.style.left = x + "px"
  	})
  	document.addEventListener('click',function (e) {
  		ul.style.display = "none"
  		e.stopPropagation()
  	})
  	ul.addEventListener('click',function (e) {
  		console.log(e.target.innerHTML)
  	})
  </script>
  ```

  



## 事件

+ 鼠标事件

  click	单击

  ```
  box.onclick = function(){
  	...
  }
  ```

  dblclick	双击

  mouseover	鼠标移入（移到子元素有影响）

  mouseout	鼠标移出（移到子元素有影响）

  mouseenter	鼠标移入（不向上传播）

  mouseleave	鼠标移出（不向上传播）

  mousemove	鼠标移动

  mousedown	鼠标按下

  mouseup	鼠标抬起

+ 键盘事件

  keydown	键盘按下

  ```js
  document.onkeydown = function (e) {
      if(e.altKey == true){	//判断组合按键，按下 alt + 按键
          console.log("alt")
      }
  }
  ```

  keyup	键盘抬起

  keypress	键盘按下再抬起

+ 表单事件

  blur	失去焦点

  focus	获取焦点

  change	文本框内容改变（失去焦点触发）

  input	文本框内容改变

  submit	表单提交（专门给from标签的）

+ 浏览器事件

  load	所有资源加载完毕后

  resize	浏览器大小改变

  scroll	浏览器滚动条滚动时

+ 其他事件

  transitionend	过渡结束后触发

  animationend	动画结束后触发

## 绑定多个事件

addEventListener（顺序执行）

```js
li[0].addEventListener("click",function  () {
    console.log(this)
})
```

attachEvent（和 addEventListener 一样，只是 IE 使用的，倒序执行）

```js
li[0].attachEvent("onclick",function  () {
    console.log(this)
})
```



## 移除事件

removeEventListener

注意：要移除事件，在绑定时需要将函数封装后绑定到元素上

```js
var ul = document.getElementById("ul")
function conthis () {
    console.log(this)
}
function con1 () {
    console.log(1)
}
ul.addEventListener("click",conthis)
ul.addEventListener("click",con1)
ul.removeEventListener('click',con1)
```

detachEvent（IE 低版本移除事件）



## 事件传播

当点击一个元素的时候，会使你点击的元素以及他的所有祖先级元素的同名事件都触发。



## 事件的冒泡和捕获

冒泡：在事件的传播过程中，去依次触发父级身上的同类型事件，知道 window

捕获：在事件的传播过程中，按照父级到元素的顺序依次执行同类型事件

+ e.stopPropagation()	阻止事件传播（从自己开始不再向上传播）

  ```JS
  smallbox.addEventListener('click',function(e){
      console.log("smallbox")
      e.stopPropagation()
  })
  ```

  

+ addEventListener 的第三个参数可以改变事件的执行方式（冒泡 / 捕获）

```js
<body>
    <div id="bigbox">
        <div id="box">
            <div id="smallbox"></div>
        </div>
    </div>
</body>
<script type="text/javascript">
    var bigbox = document.getElementById("bigbox")
    var box = document.getElementById("box")
    var smallbox = document.getElementById("smallbox")
    var body = document.documentElement

    window.addEventListener('click',function(){
        console.log("window")
    },true)
    body.addEventListener('click',function(){
        console.log("body")
    },true)
    bigbox.addEventListener('click',function(){
        console.log("bigbox")
    },true)
    box.addEventListener('click',function(){
        console.log("box")
    },true)
    smallbox.addEventListener('click',function(){
        console.log("smallbox")
    },true)


</script>
```



## 事件委托 

e.target / e.srcElement	点击的目标（ IE 只能使用 srcElement ）

```js
var ul = document.querySelector("ul")
ul.addEventListener('click',function (e) {
    console.log(e.target)
})
```

用途：元素中添加的元素没有和其他兄弟元素相同的事件，但是用事件委托后新添加的元素也有相同的事件



## 循环

for

```js
for(var a= 0; a <= 10; a++){
	......
}
```

for in	循环遍历属性名

```
var obj = {
	name:"fs",
	age:22,
	sex:"man"
}
for(var key in obj){
	console.log(key)
}
```

for of（ES6新增）

while

do while

continue	结束本次循环

break	结束整个循环



## cors





## options





## VO，AO

1. 发现有代码调用了一个函数
2. 在执行这个function之前，创建一个执行上下文（execution context），也可以叫执行环境。
3. 进入创建阶段（VO创建）
   a. 初始化作用域链（scope chain）
   b. 创建变量函数（variable object / VO）
   c. 创建参数对象（arguments object，传进来的参数）,检查上下文，初始化其名字和值，以及建立引用对象的拷贝。
   d. 扫描上下文中的函数声明
   e. 为每一个扫描到的函数声明在VO中创建一个属性，命名为函数的名字，指向了存储空间中的对应函数。
   f. 如果函数名称已经存在了，这个引用指针将被重写为新的这一个。
   g. 扫描上下文中的变量声明
   h. 为每一个扫描到的变量声明在VO中创建一个属性，命名为变量的名字，初始化值为undefined。
   i. 如果变量名在内存中已经存在了，就跳过。
   j. 决定上下文中this的指向。
4. 执行阶段（VO => AO）
   a. 执行/解释上下文中的function，为变量赋值
   b. 代码按行执行

就我个人理解，他们的相应概念和包含内容如下。

scope ：变量/函数起作用的区域
scope chain : 保证对执行环境有权访问的所有变量和函数的有序访问。相当于VO + [scope]
我们可以将作用域定义为一套规则，用来管理引擎如何在当前作用域以及嵌套的子作用域中根据标识符名称进行变量查找，作用域链是这套规则的具体实现。

execution context = {VO, this, [scope]}

this : 函数/方法的拥有者



## Math

如果传递的不是数字，将会把传入的值自动转化为数字

abs()	获取绝对值

```js
console.log(Math.abs(-1))
```

ceil	向上取整

floor	向下取整

round	四舍五入

max/min	获取最大值/最小值

```js
console.log(Math.max(1,2,3,5,6,5,8,8,88))
```

sqrt/pow	开平方/

```js
console.log(Math.sqrt(4))
console.log(Math.pow(4,2))
```

random	获取 0-1 之间的随机数

```
//获取n-m之间的随机整数
//Math.round(Math.random()*(m-n)) + n)
console.log(Math.round(Math.random()*9 + 1))
```

## 数组

+ 数组的要点

  方法的作用和含义

  方法的实参

  方法的返回值

  原来的数组是否会发生改变

+ 增删改

  （都会改变原数组）

  push	数组末尾添加

  ```js
  var arr = [1,2,3,4,5]
  arr.push(6,{name:"fs"},[11,22])
  console.log(arr)
  ```

  arr[arr.length]	数组末尾添加

  ```js
  arr[arr.length] = "fs"
  ```

  unshift	数组开头加

  ```js
  arr.unshift(6)
  ```

  shift	删除第一项

  ```js
  arr.shift()
  ```

  pop	删除最后一项

  ```js
  arr.pop()
  ```

  arr.length--	删除最后一项

  ```js
  arr.length--
  ```

  splice	实现数组的增删改

  ```js
  arr.splice(m,n)	//从 m 位开始删除 n 位，n 不写就删除到末尾
  arr.splice(0)	//清空数组
  arr.splice(arr.length-1)	//删除最后一项
  arr.splice(0,1)	//删除第一项
  arr.splice(n,m,x)	//把 n 到 m 位 用X代替
  arr.splice(arr.length,0,"aaa")	//给数组末尾添加 “aaa”
  arr.splice(0,0,"aaa")	//给数组开始添加 “aaa”
  ```

+ 数组的查询和拼接

  （不改变原数组）

  slice	查询

  ```js
  arr.slice(n,m)	//从索引 n 开始找到索引为 m 的地方，不包含 m 这一项
  arr.slice(n)	//从 n 项找到末尾，如果 n 为负数则倒数
  var newarr = arr.slice(0)	//克隆数组（浅克隆）
  ```

  concat	数组拼接

  ```js
  var arr1 = [1,2,3,4,5]
  var arr2 = [6,7,8]
  var arr = arr1.concat(arr2)
  ```

  toString	把数组转化为字符串

  ```js
  var arr1 = [1,2,3,4,5]
  var arr = arr1.toString(arr2)	//将数组转化为字符串，用逗号隔开
  ```

  join	把数组转化为字符串

  ```js
  var arr1 = [1,2,3,4,5]
  var arr = arr1.join(指定符号)	//将数组转化为字符串，用指定的符号隔开隔开
  ```

+ 检测数组是否包含某一项

  indexOf / lastIndexOf

  ```js
  var arr1 = [1,2,3,4,5]
  var arr = arr1.indexOf(检索的值)	//从第一位开始找，返回检索值在数组中的索引，没有则返回 “-1”
  var arr = arr1.indexOf(检索的值,要查找的位置)	//从某一位开始查找，返回检索值在数组中的索引，没有则返回 “-1”
  var arr = arr1.lastIndexOf(检索的值)	//从最后一位开始找，返回检索值在数组中的索引，没有则返回 “-1”
  ```

  includes

  ```js
  var arr1 = [1,2,3,4,5]
  var arr = arr1.includes("2")	//检测检索值在数组中存在，返回布尔值
  ```

+ 排序/排列

  reverse	把数组倒过来排列

  ```js
  
  ```

  sort	数组排序

  ```js
  arr.sort()		//按照字符排序
  arr1.sort((a,b)=>{return(a-b)})		//从小到大排序
  ```

+ 遍历

  forEach	遍历数组

    ```js
    //map，filter，find，reduce，some，every,......都是遍历
    var arr1 = [18,3,4,2]
    arr1.forEach((item,index)=>{
        console.log(item,index)
    })
    //item 为每一项，index为下标
    ```

  map	映射数组（对数组的每一项操作，完成后放到一个新数组中返回）

  ```js
  var arr = [1,2,3]
  var arr1 = arr.map(function (item,index,arr) {
      return item + 10
  })
  console.log(arr)	//[1,2,3]
  console.log(arr1)	//[11,12,13]
  ```

  filter	按条件返回

  ```js
  var arr = [1,2,3,4]
  var arr1 = arr.filter(function (item,index,arr) {
      return item > 2
  })
  console.log(arr)	//[1,2,3,4]
  console.log(arr1)	//[3,4]
  ```

  some	循环判断（每次 return 结果，要么为 true ，要么为 false 只要结果有一次为 true 最终结果就为 true）

  ```js
  var arr = [1,2,3,4]
  var arr1 = arr.some(function (item,index,arr) {
      return item > 2
  })
  console.log(arr1)	//true
  ```

  every	循环判断，和some类似，但需要所有结果都为 true ，最终结果才为 true（每次 return 结果，要么为 true ，要么为 false 要所有结果都为 true 最终结果就为 true）

  ```js
  var arr = [1,2,3,4]
  var arr1 = arr.every(function (item,index,arr) {
      return item > 2
  })
  console.log(arr1)
  ```

  

+ 其他

  eval	把字符串变为 js 表达式

  ```
  eval()
  ```

## 字符串

​	字符串的方法都不改变原始字符串
​    length	字符串长度

```js
atr.length
charAt / charCodeAt	通过索引获取指定位置的字符 / 该字符的 ASCII 值
let str = "abbccdddeeeefffff"
console.log(str.charAt(5))	//返回改位的字符串，如果没有则返回空字符串
console.log(str.charCodeAt(5))	//返回改位的字符串的 ASCII，如果没有则返回 NaN
```




+ 字符串截取

    substr(n,m)	从索引 n 开始截取 m 个

    ```js
    let str = "abbccdddeeeefffff"
    str.substr(1,3)	//bbc
    ```

    substring(n,m)	从索引 n 开始截取到索引 m 

    ```js
    let str = "abbccdddeeeefffff"
    str.substring(1,3)	//bb
    ```

    slice(n,m)	从索引 n 开始截取到索引 m （支持负数作为参数）

    ```js
    let str = "abbccdddeeeefffff"
    str.substring(-3,-1)	//ff
    ```

+ 验证字符是否存在

    indexOf(x,y)	验证 X 第一次出现的索引，y控制查找的起始位置，返回索引，没有则返回 -1

    ```js
    let str = "sdfsadsafdsadfsafd"
    console.log(str.indexOf("a"))
    ```

    lastIndexOf(x)	最后一次出现的位置，返回索引，没有则返回 -1

    ```js
    let str = "sdfsadsafdsadfsafd"
    console.log(str.lastIndexOf("a"))
    ```

    includes	验证是否包含该字符串

    ```js
    let str = "sdfsadsafdsadfsafd"
    console.log(str.includes("z"))
    ```

+ 大小写转化

    toUpperCase/toLowerCase	字符的大小写转化

    ```js
        let str = "sdfsadsafdsadfsafd"
        console.log(str.toUpperCase()）	//转大写
        console.log(str.toLowerCase())	//转小写
    ```

+ 分割字符串

    split	分割字符串（支持正则表达式）

    ```js
    let str = "sdfsadsafdsadfsafd"
    console.log(str.split("a"))	//把字符串按照 a 分割为数组
    ```

    replace	实现字符串替换（在不使用正则表达式的情况下，执行一次只替换一次字符）

    ```js
    let str = "sdfsadsafdsadfsafd"
    console.log(str.replace("a","-"))
    ```

+ ASCLL 码值转换

  字符转ascii码：用charCodeAt();

  ```js
  var str = "A";
  str.charCodeAt();  // 65
  ```

  ascii码转字符：用fromCharCode();

  ```js
  var num = 97;
  String.fromCharCode(num);  // 'a'
  ```

  

+ 其他

    match

    localCompare

    trim / trimLeft / trimRight

    ...



## 获取时间

new Date	获取时间

```js
var time = new Date()
time.getFullYear()	//获取年
time.getMonth()	//获取月	0-11 一月到十二月
time.getDate()	//获取日
time.getDay	//获取星期	0-6 为周日到周六
time.getHours()	//获取时
time.getMinutes()	//获取分
time.getSeconds()	//获取秒
time.getMilliseconds()	//获取毫秒
time.getTime()	//获取时间戳（当前日期距离1970/1/1 00:00:00 之间的时间戳）
time.toLocaleString()	//获取年月日的字符串
time.toLocaleDateString()	//获取年月日时分秒的字符串
time.toString()	//将Date变为字符串的字符串
```

new Date()	传值

```js
let time = new Date("2019/1/1")		//时间格式化，将参数转为标准格式的时间字符串
```



## DOM及其基础操作

获取dom的方法

```
document.querySelector()
document.querySelectorAll()
```

### 节点

+ 元素节点

  nodeType：1

  nodeName：大写名称

  nodeValue：null

  + 文本节点

    nodeType：3

    nodeName：“ #text ”

    nodeValue：文本内容

    nodeValue：文本内容

  + 注释节点

    nodeType：8

    nodeName：“ #commen ”

    nodeValue：注释内容

  + 文档节点

    nodeType：9

    nodeName：“ #document ”

    nodeValue：null

### 增删改查

+ 查

  childNodes：获取所有子节点

  children：获取所有的元素子节点（元素标签集合）

  parentNode：获取父节点

  ```js
  var parent = document.getElementById("haha").parentNode
  ```

  firstChild：获取第一个子节点

  lastChild：后去最后一个子节点

  firstElementChild：获取第一个元素节点

  lastElementChild：获取最后一个元素节点

  previousSibling：获取上一个哥哥节点

  nextSibling：获取下一个弟弟节点

  previousElementSibling：获取上一个哥哥元素节点

  nextElementSibling：获取下一个弟弟元素节点

+ 增

  createElement	创建元素标签

  createTextNode	创建文本对象

  appendChild	把元素添加到容器的末尾

  ```js
  <body>
  	<div class="bigbox"></div>
  </body>
  <script type="text/javascript">
  	var box = document.createElement("div")	//创建一个 div 赋值给box
  	var bigbox = document.getElementsByClassName("bigbox")[0]	//获取类名为 bigbox 的元素
  	let text = document.createTextNode("我是文本")	//创建一个文本节点
  	box.appendChild(text)	//将文本节点插入到 box 的节点末尾
  	bigbox.appendChild(box)	//将 box 插入到 bigbox 元素末尾
  </script>
  ```

  insertBefore	把元素添加到指定容器中指定元素的前面

  ```js
  <body>
  	<div class="bigbox">
  		<div id="haha">哈哈</div>
  	</div>
  </body>
  <script type="text/javascript">
  	var bigbox = document.getElementsByClassName("bigbox")[0]
  	var haha = document.getElementById("haha")
  	var text = document.createTextNode("文本")	//创建文本节点
  	bigbox.insertBefore(text,haha)	//将 text 放在“哈哈”之前
  </script>
  ```

  cloneNode(true/false)	克隆元素或者节点（深克隆/浅克隆）（是否克隆后代元素）

  ```js
  <body>
  	<div class="bigbox">
  		<div id="haha">哈哈</div>
  	</div>
  </body>
  <script type="text/javascript">
  	var bigbox = document.getElementsByClassName("bigbox")[0]
  	var haha = document.getElementById("haha")
  	var newhaha = haha.cloneNode(true)
  	bigbox.append(newhaha)
  </script>
  ```

  innerHTML/innerText	字符串拼接插入

  ```
  <body>
  	<div class="bigbox"></div>
  </body>
  <script type="text/javascript">
  	var bigbox = document.getElementsByClassName("bigbox")[0]
  	bigbox.innerHTML = "<div id='haha'>哈哈</div>"
  </script>
  ```

  

+ 删

  removeChild 	移除容器中的元素

  ```js
  <body>
  	<div class="bigbox">
  		<div id="haha">哈哈</div>
  	</div>
  </body>
  <script type="text/javascript">
  	var bigbox = document.getElementsByClassName("bigbox")[0]
  	var haha = document.getElementById("haha")
  	bigbox.removeChild(haha)
  </script>
  ```

+ 改

  自定义属性

  setAttribute/getAttribute/removeAttribute	设置/获取/移除元素的自定义属性

  ```js
  haha.setAttribute(属性名,属性值)
  ```

  replaceChild	替换节点

  ```js
  <body>
      <div id="box">
          <h2>h2</h2>
          <span id="span">span</span>
      </div>
  </body>
  <script type="text/javascript">
      var span = document.getElementById("span")
      var box = document.getElementById("box")
      var p = document.createElement("p")
      p.innerHTML = "p"
  
      box.replaceChild(p,span)
  </script>
  ```

  style	修改行内样式

  ```js
  <body>
  	<div class="bigbox">bigbox</div>
  </body>
  <script type="text/javascript">
  	var bigbox = document.getElementsByClassName("bigbox")[0]
  	bigbox.style.color = "red"
  </script>
  ```

  className	设置类名

### 浏览器

+ 浏览器尺寸（不包含滚动条）

  ```js
  document.documentElement.clientWidth
  document.documentElement.clientHeight
  ```

  



## BOM

+ 弹出层

  + alert	弹出提示框，只有确定

  + confirm	弹出询问框，确定/取消，有返回值，返回 true / false

    ```js
    var a = prompt("请输入点东西")
    console.log(a)
    ```

  + prompt	弹出输入框，接收参数，且有返回值，返回输入的内容，不输入则返回空字符串，取消后

    ```js
    var a = prompt("请输入点东西")
    console.log(a)
    ```

    

+ 浏览器

  + 尺寸

    innerHeight / innerWidth	屏幕宽高（半酣滚动条）

    ```js
    console.log(window.innerWidth)
    ```

    

+ 地址栏

  + loction

    href	获取当前地址栏的值，也可以赋值跳转页面

    ```js
    console.log(location.href)
    window.location.href = "http://www.baidu.com"
    ```

    reload	重新加载页面方法（相当于）

    

+ 历史记录

+ 获取浏览器版本



## JS操作盒子模型属性

+ 获取元素样式信息

方法：window.getComputedStyle(元素，[伪类] / 元素.currentStyle)

​	getCumputedStyle	获取当前元素所有经过浏览器计算过的样式（在IE6~8 中不兼容，需要基于 currentStyle 来获取）

```
window.getComputedStyle(元素，伪类)
```



+ client
  + width / height	bigbox元素宽度 + padding宽度，内容溢出不影响，获取的结果都没有单位(px)，结果是整数（自动四舍五入）
  
    ```js
    <body>
    	<div id="bigbox">bigbox</div>
    </body>
    <script type="text/javascript">
    	var bigbox = document.getElementById("bigbox")
    	console.log(bigbox.clientWidth)	//bigbox元素宽度 + padding宽度
    	console.log(document.documentElement.clientWidth)	//浏览器宽度
    	console.log(document.body.clientWidth)	//浏览器宽度
    </script>
    ```
  
  + top / left	获取左边框 / 下边框大小
+ offset
  - width / height	 bigbox元素宽度 + padding宽度 + border宽度
  
    ```js
    var offWidth = bigbox.offsetWidth
    ```
  
    
  
  - top / left      距离其夫参照物的上 / 左偏移
  
  - parent     获取其父参照物，不一定是父元素
+ scroll 
  + width 

  +  height	在没有内容溢出的情况下，获取的结果和 client 一样，有内容溢出的情况下获取结果约等于实际高度，设置 overflow:hidden 对结果有影响

    ```js
    console.log(document.documentElement.clientWidth)	//整个页面真实高
    console.log(document.body.clientWidth)	//整个页面真实高度
    ```

  + top / left     竖向 / 横向滚动条卷曲的距离（所有盒子模型属性中，只有这两个属性为可读写属性，其余的都是只读不可写属性）



## 图片懒加载

1. 结构中，用一个盒子包裹图片
2. IMG 的 SRC 中不设置任何图片地址，可以将图片的真是地址存放到自定义属性当中，最开始让图片隐藏
3. 当浏览器窗口完全展示到图片位置时候再加载图片（第一屏图片一般都会延迟来等待其他资源先加载）
4. 图片显示条件
   + A：盒子底边距的距离：盒子高度 + 盒子距BODY的上偏移
   + B：浏览器底边距离BODY的距离：一屏幕的高度 + 卷曲的高度
   + A <= B （盒子完全出现再视野中）

5. 让图片显示

   + 获取自定义的属性值，复制给 src 属性，当图片能正常加载后让图片显示

6. 注意：加载过的图片不需要重新加载，

   ```
   
   ```

   



## 作用域 



## 作用域链



## 面向对象



## 类



## 原型链



## this

在作用域中使用的关键字，不看定义，只看调用

+ this 指向

    1. 全局调用	函数名（）	this => window
    2. 对象调用	对象 . 函数名（）	this => 这个对象
    3. 定时器处理函数	this => window
    4. 事件处理函数	this => 事件源（）
    5. 自执行函数 	this => window
    6. 剪头函数	this => 上一级作用域（不受 call ，apply ， bind 等任何影响）

    ```js
    function  fn() {
        console.log(this)	//这里的 this 为window
    }
    fn()
    ```

    ```js
    obj = {
        name: "fs",
        fn: function  () {
            console.log(this)	//this 为 obj 对象
        }
    }
    obj.fn()
    ```

+ 改变 this 指向

    1. call	函数立即执行

       函数名 . call（this 需要指向的东西，正常参数 1，正常参数 2， ......）

       注意：call（）中不传参或者传入 null 后 this 指向 window 

       ```
       function A (name,age) {

           this.name = name;
           this.age = age;

       }
       var obj = {};
       A.call(obj)
       var a = new A('fs',100);
       console.log(obj);
       ```

    2. apply	函数立即执行

       函数名 . apply（this 需要指向的东西，[参数 1，参数 2，......] ）

       注意：使用方法和 call 类似， apply 只传两个参数，第二个是一个数组，数组中是正常的参数

       例：（数组中取最大值）

       ```js
       var num = [1,2,3,5,6,5,4,8,7,9,55,12]
       var max = Math.max(1,2,3,5,6,5,4,8,7,9,55,12)
       var max1 = Math.max.apply(num)
       console.log(max,max1)	//max 和 max1 的结果是一样的
       ```

    3. bind	返回一个改变好 this 指向的函数，需要变量接收

       函数名 . bind（this 需要指向的东西）

       ```js
       function a () {
           console.log(this);
       }
       var num = 111;
       var bindfn = a.bind(num)
       bindfn()
       ```
    
    4. 

## 回调函数



## 数据劫持

```js
	<body>
		<div class="test"></div>
		<input type="text" name="" id="" value="" />
	</body>
	<script type="text/javascript">
		
		var div = document.querySelector("div");
		var inp = document.querySelector("input");
		var obj = {
			name:"test1"
		}
		
		Object.defineProperty(obj,"name",{
			get(){
				
			},
			set(){
				
			}
		})
		 
		div.innerHTML = obj.name
		inp.oninput = function(){
			obj.name = this.value
		}
	</script>
```



## 同步异步编程



## 设计模式



## 函数的防抖节流



## 柯里化函数



## 深度克隆数组



## 数组塌陷问题



删掉数组中的第一项后第二项变为第一项



## 阻止默认事件

+ 阻止 a标签 的默认行为

  ```js
  <a href="javascript:;">a标签</a>
  ```

+ 阻止表单默认事件

  ```
  //再事件中加以下代码，需要参数 e
  e.preventDefault()
  ```

  



## 二维数组





## formdata





# ES6

## 变量

+ let	变量

不可重复声明

块级作用域，任何一个大括号就可以限制作用域

```js
//循环绑定
<body>
	<button>我是1</button>
	<button>我是2</button>
	<button>我是3</button>
	<button>我是4</button>
	<button>我是5</button>
</body>
<script type="text/javascript">
	var btn = document.querySelectorAll("button")
	for(let a = 0; a < btn.length; a++){
		btn[a].onclick = function () {
			console.log(a)
		}
	}
</script>
```



+ const	常量

不可重复声明

块级作用域



## 类

class

定义一个类（相当于构造函数，但不可直接执行，首字母必须大写，没有小括号）

```js
class Person{
    //类的属性，不需要形参
    age = 20;

    //我就是 es5 的构造函数体的那个函数，用来接收形参
    constructor (name,sex){
        this.name = name;
        this.sex = sex
    }


    //直接写方法，不用在 proto 上边找
    sayHi(){
        console.log("我是 Person 上的方法 sayHi");
        console.log(this.name);
    }
}

var p1 = new Person("fs")
console.log(p1)
p1.sayHi()
```



## 函数

+ 箭头函数

箭头函数中没有 arguments，用 ... 代替（一般写为 ...arg ）

任何方法都不可改变剪头函数的 this 指向

()=>{}

只有一个参数，小括号可省略

只有一个return，大括号可省略

+ 参数展开 （...name）

收集剩余的参数，只能放最后

例：

```js
function aa (a,...b) {
    console.log(a,b)
}
aa(1,2,3,4,5,6)
```

+ 展开数组

输出数组中的每一项，不可将展开的内容赋值给变量

```
var bb = [3,2,1]
console.log(...bb)
//输出: 3 2 1
```

+ 自执行函数

  不污染全局，this 指向 window（在对象中也是指向 window）

  ```js
  (function (){})()
  ~function (){}()
  !function (){}()
  ```

  ```js
  (function function_name (w) {
      var name = "fs",age = 18
      w.sex = "男"
      console.log(name,age)
      console.log(sex)
  })(window)
  console.log(name,age)	//在这里访问不到
  console.log(sex)	//在这里可以访问
  ```




## 解构赋值

定义变量的一种方法，

左右两边解构一致，声明和赋值必须在一句话中完成，不可分开

例：

```js
let [a,b,c] = [1,2,3]
let {d,e} = {d:5,e:6}
console.log(a,b,c,d,e)
```

```js
var obj = {
    name:"fs",
    age:18,
}
var {age:a} = obj
obj.age = 20
console.log(a)
```



## 展开运算符（...）

实现数组对象的展开

数组拼接：例：

```js
var arr1 = [1,2,3]
var arr2 = [4,5,6]
var arr = [...arr1,...arr2]
console.log(arr)	//[1,2,3,4,5,6]
```

展开传参数：例：

```

```

也可展开对象



## 合并运算符（...）

写在形参和解构赋值的时候是合并运算符

注意：在箭头函数中不可省略小括号

```js
function hai (...a) {
    console.log(a)
}
hai(1,2,3,4,5)
```



## 数组

+ map （映射）

```js
var arr = [1,2,3]
var arrmap = arr.map(function (item) {
    return item +3
})
console.log(arrmap)
```

+ reduce （汇总）

例（求和）：

```js
var arr = [1,2,3,4,5,6]
var arrreduce = arr.reduce(function (a,b,c) {
    return a + b
})
console.log(arrreduce)
```

+ filter （过滤器）

例：

```js
var arr = [1,2,3,4,5,6]
var arrfilter = arr.filter(function (item) {
    return item>2
})
console.log(arrfilter)
```

+ forEach	（循环（迭代））

例：

```js
var arr = [1,2,3,4,5,6]
arr.forEach(function (item,index) {
	console.log(item,index)
})
```

## 字符串

+ sttartsWith		（判断字符串是否以...开头）

```js
var str = 'aasdfasdf';
console.log(str.startsWith('aa'))
```

+ endsWith		（判断字符串是否以...结尾）

```js
var str = 'aasdfasdf';
console.log(str.startsWith('df'))
```

+ 模板字符串

```js
var aaa = "---------"
console.log(`2222222${aaa}222222`)
```



## 面向对象

class 关键字，构造器和类分开

class 里边直接加方法

```js
class user{
    constructor(name,pwd){
        this.name = name;
        this.pwd = pwd;
    }
    showName(){
        console.log(this.name)
    }
}

var fs = new user('fs','123')
fs.showName()
```

继承

```js
class User{
    //写属性
    constructor(name,pwd){
        this.name = name;
        this.pwd = pwd;
    }
    showName(){
        console.log(this.name);
        console.log(this.age);
    }
}

//继承类
class VipUser extends User{
    constructor(name,pwd,age){
        //继承父类的属性
        super(name,pwd);

        this.age = age;
    }
}

var fs = new VipUser('fs','123',12)
fs.showName()
```



## promise

Promise.all()

Promise.all([$.ajax({}),$.ajax({}),]).then( arr=>{}, err=>{})

例：

```js
Promise.all([
    $.ajax({
        type:"get",
        url:"http://127.0.0.1:8020/test/1.txt",
        dataType:'json'
    }),
    $.ajax({
        type:"get",
        url:"http://127.0.0.1:8020/test/12.txt",
        dataType:'json'
    }),
]).then(function (arr) {
    console.log('全部成功')
    console.log(arr)
},function (err) {
    console.log('至少有一个出错')
    console.log(err)
})
```



## generator

可暂停函数

（1）函数名旁边加*

（2）yield 为暂停的地点（可返回--在 yield 后）

（3）将运行的函数赋值给变量（函数不会直接运行）

（4）next 使函数运行到下一个 yield 处暂停（可传参--在函数的 next中）

```js
function *show () {
    alert('a');

    let b = yield 999;

    alert(b);

    let c = yield b;

    alert(c)
}
var sh = show()
let d = sh.next(1)
console.log(d)

let e = sh.next(2)
console.log(e)

let f = sh.next(3)
console.log(f)
```



## JSON解析

解析的字符串中， key 和 value 必须包裹在双引号中，value 中是数字、布尔、或者 undefined 的时候可以不包裹,最后一条数据不能有逗号

+ parse 		解析（字符串转为对象）

例： 

```js
JSON.parse(str)
```

+ stringify		反解析（对象转为字符串）

例：

```js
JSON.stringify(json)
```

+ 专门存放 JSON 的文件（.json）

  

# ES7

#### 1.inclund	（检查数组中是否包含...）

例：

```js
var arr = [1,2,3,4,5]
console.log(arr.includes(5))
```

#### 2.for  of	（循环迭代，不可用于JSON）

keys	：下标

values	：值

entries	：键值对

```js
var arr = [5,99,88]
for(let i of arr){
    console.log(i)	//输出 arr 的各个值
}
console.log('----------------------------------')
for(let i of arr.keys()){
    console.log(i)	//输出 arr 的各个下标
}
console.log('----------------------------------')
for(let i of arr.values()){
    console.log(i)	//输出 arr 的各个值
}
console.log('----------------------------------')
for(let i of arr.entries()){
    console.log(i)	//输出 arr 的各个键值对（下标：值）
}
```

#### 3.幂

```js
a**3	//a 的 3 次幂
```

#### 4.数组

padStart 	（左边补东西到一共多少位）	

```js
console.log('(' + '123'.padStart(6,'0') + ')')
```

padEnd		（右边补东西到一共多少位）

#### 5.async  await	（类似generator  yield）

例：

```
async 
```

 
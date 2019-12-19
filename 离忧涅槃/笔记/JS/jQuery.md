文档：http://jquery.cuishifeng.cn/

书籍：《锋利的jQuery第二版》

## 优点

1. 选择器

2. 隐式迭代

3. 链式编程



## 选择器

+ 选择器

$()

```js
$("div")//获取全部
$(".class")//获取全部
$("#id")//只获取一个
```

jQuery()

```js
jQuery("div")
jQuery(".class")
jQuery("#id")
```

+ 特殊选择器

    1. :first	获取符合条件的第一个

    ```
    $("ul > li:first")
    ```

    2. :last	获取符合条件的最后一个

    3. :eq	获取符合条件的第几个

    4. :odd	获取符合条件的索引为奇数的所有元素

    5. :eve	获取符合条件的索引为偶数的所有元素

+ 筛选器

  当用选择器选择完毕后，用来筛选的

  1. first()	第一个

  ```js
  var inp = $("ul li")
  console.log(inp.first())
  ```

  2. last()	最后一个

  3. eq()	第几个

  4. prev()	上一个

  5. prevAll()	上边所有

  6. next()	下一个

  7. next()	下边所有

  8. siblings()	所有兄弟元素

  9. parent()	父元素

  10. parents()	所有祖先元素

  11. find()	查找

      ```js
      var inp = $("ul")
      console.log(inp)
      console.log(inp.find("li"))
      ```

## 操作元素内容

1. html()

   不传参是获取，传递参数时是设置

   ```js
   var inp = $("div").html()
   var inp = $("div").html("测试")
   ```

   

2. test()

3. val()

   专门操作表单元素

## 操作元素的属性

有两套方法

+ attr

  不管是自定义的还是原生的都能显示在标签上

  attr()	第二个参数不传数为获取，传递参数为设置

  ```js
  inp.attr("id")//获取
  inp.attr("id","iest")//设置
  ```

  removeAttr()

  ```js
  inp.removeAttr("id")//删除
  ```

  

+ prop

    只有是原生的属性才能显示在标签上

    prop()	第二个参数不传数为获取，传递参数为设置

    ```js
    inp.prop("id")//获取，如果是自定义属性，只能获取 prop 添加的属性
    inp.prop("id","iest")//设置
    ```

    removeProp()

    ```js
    inp.removeProp("id")//删除，只能移除自己设置的，class/id无法删除
    ```

## 操作类名

+ addClass	添加

  

+ removeClass	删除

+ hasClass	判断有无

+ toggleClass	切换

## 操作元素样式

+ css

  ```js
  inp.css("color")//获取，可获取行内和非行内样式
  inp.css("font-size","20px")//设置方法1
  inp.css({fontSize:"20px"})//设置方法2，使用小驼峰写法
  ```

## 事件

+ on	绑定事件

  1. on('事件类型' , 事件处理函数)

      ```js
      inp.on("click",function(){
          console.log(1)
      })
      ```

  2. on('事件类型' , 进行事件委托，事件处理函数)

      ```js
      test.on("click","li",function(e){
          console.log(this)
      })
      ```

  3. on('事件类型' , 进行事件委托，传递参数，事件处理函数)

     这里的传参主要是给事件传参
     
     ```js
     test.on("click","li",{name:"饭"},function(e){
         console.log(e)
     })
     ```
     
     

+ one	只能执行一次的事件

  1. on('事件类型' , 事件处理函数)

     ```js
     inp.one("click",function(){
         console.log(1)
     })
     ```

  2. one('事件类型' , 进行事件委托，事件处理函数)

     使用事件委托后，所有元素只能执行一次，第一个元素执行后其他元素的无法执行

     ```js
     test.on("click","li",function(e){
         console.log(this)
     })
     ```

+ hover(移入函数，移出函数)

  ```
  hover(function(){},function(){})
  ```

+ off	取消事件

  ```js
  $("ul").off("click",fn)//取消某个事件
  $("ul").off("click")//取消某所有事件
  ```

+ trigger	元素的事件执行一次

  ```js
  $("ul").trigger("click")
  ```

## 节点

+ 创建

  $()

  ```js
  $('<p></p>')
  ```

+ 插入

  + 内部插入（父子关系）

    1. append	插入到最后边

       ```js
       //父元素.append(子元素)
       ```

    2. appendto	插入到最后边

       ```js
       //子元素.append(父元素)
       ```

    3. prepend	插入到最前边

       ```js
       //父元素.prepend(子元素)
       ```

    4. prependTo	插入到最前边

       ```js
       //子元素.prepend(父元素)
       ```

  + 外部插入（兄弟关系）

    1. after()	添加在某个页面元素的后边

       页面元素.after(要添加的元素)

    2. insertAfter()	把要添加的元素插入到某个页面元素的后边

       要添加的元素.after(页面元素)

    3. before()	添加在某个页面元素的前

       页面元素.before(要添加的元素)

    4. insertBefore()	把要添加的元素插入到某个页面元素的前边

       要添加的元素.insertBefore(页面元素)

+ 替换

  1. replaceWith

     旧节点.replaceWith(新节点)

     注意：会把选择到的所有节点都替换

     ```js
     <body>
         <div>
             <p>原来的</p>
         </div>
     </body>
     <script type="text/javascript">
         var p = $('<p>新的</p>')
         $('div p').replaceWith(p)
     </script>
     ```

  2. replaceAll()

     新节点.replaceAll(旧节点)

+ 删除

  1. remove	移除自身

     元素.remove()

     ```js
     $('div').remove()
     ```

  2. empty()	把自己变成空标签

     ```js
     $('div').empty()
     ```

+ 克隆

  clone	克隆节点

  原元素.clone(true/false , true/false)

  第一个参数：是否克隆事件，第二个参数：是否克隆子元素事件

  ```js
  $("div").clone(true)//默认false，
  ```

## 获取元素尺寸

1. width() / height()	

   内容区域，不管子元素是否溢出

   ```js
   $('p').width()
   ```

2. innerWidth() / innerHeight()	

   内容+padding，不管子元素是否溢出

3. outerWidth() / outerHeight()	

   内容+padding+border，不管子元素是否溢出

4. outerWidth(true) / outerHeight(true)	

   内容+padding+border+margin，不管子元素是否溢出

## 元素偏移量

+ offset	相对页面尺寸

  获取

  ```js
  console.log($('p').offset())
  ```

  设置

  ```js
  $('p').offset({left:100,top:100})
  ```

+ psition()	是一个只读的属性，向上寻找定位父级比较相对位置

  ```
  console.log($('p').position())
  ```

+ scrillTop() / scrollLeft()	浏览器卷曲的宽度和高度

  ```js
  $(window).scrollTop()//获取
  $(window).scrollTop(0)//设置
  ```

## 动画

+ 基础动画

    1. show

	  show(时间-毫秒，运动曲线，运动结束后的回调函数)

      ```js
  $('p').hide(500,'linear',function(){
          console.log("结束")
  })
    ```
  
    2. hide
    
    3. toggle

+ 折叠动画

  1. slideDown()

  2. slideUp()

  3. slideToggle()

     slideToggle(时间-毫秒，运动曲线，运动结束后的回调函数)

     ```js
     $('p').slideToggle(1000,'linear',function  () {
         console.log('运动结束')
     })
     ```

+ 淡入淡出

  1. fadeIn()

  2. fadeOut()

  3. fadeToggle()

     fadeToggle(时间-毫秒，运动曲线，运动结束后的回调函数)

     ```js
     $('p').fadeToggle(1000,'linear',function  () {
         console.log('运动结束')
     })
     ```

  4. fadeTo()	去到一个指定的透明度

     fadeToggle(时间-毫秒，透明度,运动曲线，运动结束后的回调函数)

     ```js
     $('p').fadeTo(1000,0.5,'linear',function  () {
         console.log('运动结束')
     })
     ```

+ 自定义动画

  animate

  animate(样式，时间，运动曲线，结束函数)

  ```js
  $('p').animate({
      width:200,
      height:500,
  })
  ```

+ 结束动画

  1. stop()	直接让动画停止

     ```js
     $('p').stop()
     ```

  2. finish()	让动画直接完成

     

## Ajax

1. get

2. post

3. ajax

   ```js
   $.ajax({
       url: "http://127.0.0.1/php/log.php", //请求的url地址
       dataType: "text", //返回格式为json
       async: true, //请求是否异步，默认为异步，这也是ajax重要特性
       data: {
           "test": "test"
       }, //参数值
       type: "post", //请求方式
       beforeSend: function(data) {
           //请求前的处理
       },
       success: function(req) {
           //请求成功时处理
       },
       complete: function(data) {
           //请求完成的处理
   
       },
       error: function(data) {
           //请求出错处理
           //失败回调，这是jQuery判定的失败，写了数据类型后，如果类型不正确也属于失败
       }
   //以下一般不用
   //			dataType: 'json', //期望接收的数据类型
   //			cache: false, //是否缓存
   //			timeOut: 3000， //请求超时时间
   });
   ```

4. jsonp

   jsonp 请求默认不缓存

   ```js
   $.ajax({
       type:"get",
       url:"http://127.0.0.1",
       async:true,
       //以下为jsonp特有的参数
       jsonp:'cb',//设置向后端传递的 key
       jsonpcallback:'fn',//向后端传递的函数名
   });
   ```

5. 钩子函数

   1. ajaxStart()
   
      在一个代码块里面请求开始的时候触发，如果有多个请求，只触发一次

      ```js
      $(window).ajaxStart(function () {
              console.log('开始请求')
      })
      ```
   
   2. ajaxSend()
   
      每一个请求前触发
   
   3. ajaxSuccess()
   
      只要有请求成功就触发
   
   4. ajsxError()
   
      只要有一个请求失败就触发
   
   5. ajaxComplrtr()
   
      只要有一个请求完成就触发，不管成功失败
   
   6. ajaxEnd()
   
      在一个代码块中请求结束的时候触发，多个请求的话在最后一个结束后触发
   
      

## 入口函数

在页面结构加载完成后执行，和 js 中的 window.onload 不同，js 中会在全部资源加载完成后才执行，包括图片等文件

ready

```js
$(window).ready(function(){})
//可简写为
$(function(){})
```



## 多库并存

+ jQuery.noConflict()

  交出 $ 的控制权

+ jQuery.noConflict(true)

  交出 $ 和 jQuery 的控制权

+ var JQUERY = jQuery.noConflict(true)

  交出 $ 和 jQuery 的控制权，用新的变量 JQUERY 来替代

  

## 遍历

each()

```js
var a = [1,2,3,4,5];
$(a).each(function (index,item) {
    console.log(index,item)
})
```



## 扩展

+ 给全局扩展

  $.扩展内容()

  ```js
  $.extend({
  	max:function (){
  		console.log('我是全局扩展的 max 函数')
  	}
  })
  ```

+ 给元素扩展

  $.fn.扩展内容()

  ```js
  $.fn.extend({
  	max:function (){
  		console.log('我是元素扩展的 max 函数')
  	}
  })
  ```

  

## 表单验证

网站：https://www.runoob.com/jquery/jquery-plugin-validate.html

下载地址：http://static.runoob.com/download/jquery-validation-1.14.0.zip

+ 操作步骤

  1. 引入jq，Validation，messages_zh(中文包可选择不要)

  2. 定义规则

     ```js
     $("#表单ID").validate({
     	
     })
     ```

+ jQuery拿到 form 中内容的方法

  ```js
  var formdatas = $(form).serialize()
  console.log(formdatas)
  ```

  
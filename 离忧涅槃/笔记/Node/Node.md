

## 安装

下载网站：http://nodejs.cn/download/

最好下载安装包，直接下一步，如果下载二进制文件需要配置

安装

安装好后在 cmd 中用  `node -v` 测试



## 模块

### 1.自定义模块

+ 导出

    (1) exports	可导出多个

    ```js
    function add(){
        console.log('this is add');
    }
    var a = 100;
    
    exports.a = a;
    ```

    (2) module.exports	接收一个对象，向里边添加成员的时候就是要导出的内容

    ```js
    var a = 123
    var arr = [1,2,3]
    var funn = function () {
        return '1122'
    }
    
    module.exports = {
        a:a,
        arr:arr,
        funn
    }
    ```

+ 导入	（require）

    ```js
    var aa = require('./fs')

    console.log(aa.a)
    console.log(aa.arr)
    console.log(aa.funn())
    ```

### 2.内置模块

+ http（服务）

  开启服务流程：

    1. var http = require('http')	 	引入http模块

    2. var server = http.createServer()		创建服务

    3. server.on()		配置服务器函数

    4. req.url		接收到的请求参数

    5. res.setHeader('Content-Type','text/html;charset=utf-8')		解决乱码

    6. res.write()		向前端发送内容

    7. res.end()		结束请求

    8. server.listen()		监听

        ```js
        var http = require('http')	//引入http模块

        var server = http.createServer()	//创建服务

        //写服务的函数
        server.on('request',function (req,res) {
            res.setHeader('Content-Type','text/html;charset=utf-8')	//解决乱码问题
            
            console.log(req.url)//输出前端请求的路径
            
            if(req.url == '/1'){//判断请求内容
                res.write('参数正确')//返回的内容，后边内容可继续返回
            }
            else{
                res.write('参数错误')
            }
      res.end('')//返回的内容，后边内容不可继续返回
        })
        
        //创建监听
        server.listen(8080,function(){
            console.log('启动服务成功')
        })
        ```

+ 请求对象（request）

    1. req.headers		//获取请求头信息（对象）

    2. req.rawHeaders		//获取请求头信息（数组）

    3. req.httpVersion		//获取http版本

    4. req.method		//获取请求方法

    5. req.url		//获取请求路径（不含网址）

+ 响应对象（response）

    

#### (2) fs	（文件操作）

+ 写入

    完全覆盖，如果没用该文件则创建一个文件再写入，需要追加时可先读取再拼接写入

    ```js
    var fs = require('fs')
    
    //writeFileSync 为同步写入，一般不用
    fs.writeFile('./b.js','你好',function(err){
        if(!err){
            console.log('书写成功')
        }
    })
    ```

+ 读取

	默认读取到的为 Buffer 字符串，需要改变字符编码格式

    ```js
  var fs = require('fs')

  //readFileSync 为同步读取，一般不用
  fs.readFile('./b.js','utf8',function(err,data){
    if(!err){
        console.log(data)
    }
    else{
        console.log(err)
    }
  })
    ```



#### (3) url	（路径）

parse

```js
var url = require('url')
var data = 'http://www.baidu.com?name=樊&age=18'

console.log(url.parse(data))
 var aa = url.parse(data,true).query
console.log(aa)

```



#### (4) path	（路径处理）

1. __dirname

   显示当前文件所在路径

2. __filename

   当前文件的路径

4. join

   路径拼接

   ```js
   var path = require('path')
   
   var res = path.join('a','b','c')
   console.log(res)
   ```

5. path.basename()	取最后一层

6. path.dirname(u)	去掉最后一层

例：

```js
var path = require('path')
var u = 'C:/Users/pp/Desktop/node/a.js'

console.log(path.basename(u))
var u = path.dirname(u)
console.log(u)
console.log(path.basename(u))
```

#### (5) os	（操作系统）



#### (5) Express	（框架）

使用步骤

1.初始化文件

```js
npm init -y
```

2.安装模块

```js
npm install express
```

3.引入

```js
var express = require('express')
```

4.创建服务器

```js
var app = express()
```

5.配置服务器

```js
app.get('/',function(req,res){
	res.send('接到请求')
})
```

6.配置监听信息

```js
app.listen(888,function(){
	console.log('启动服务器成功，地址：127.0.0.1:888')
})
```

例：

```js
var express = require('express')
var app = express()
app.get('/',function(req,res){
	res.send('接到请求')
})
app.listen(888,function(){
	console.log('启动服务器成功，地址：127.0.0.1:888')
})
```

例2：

```js
var express = require('express')
var server = express()

server.use((req,res,next)=>{
	res.send('请求接通,参数：' + req.url)
	console.log('11')
	console.log('22')
	next()		//函数执行到next() 时先执行下一个函数
})
server.listen(81,function(){
	console.log('服务器启动成功，访问地址：fanshuai.art:81')
})
```

6.优化路由

### 3.第三方模块


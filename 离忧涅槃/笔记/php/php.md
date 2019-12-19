## 注意

每句话必须加 `;` 

开头加 `header('content-type:text/html;charset=utf-8;');` 可显示中文

```php
header('content-type:text/html;charset=utf-8;');
```



## php书写位置

php写在 .php 后缀的文件里边，文件必须以 `<?php` 开头，以 `?>` 结尾的符号对里面

>```php+HTML
><?php
>    // 单行注释
>
>    /* 多行注释 */
>
>    # 注释 php 自己的注释
>    
>?> 
>```



## 定义变量

```php
$num = 100;	//定义数字
$str = '12345';	//定义字符串
$boo = true;	//定义布尔

echo $num;	//输出
```



## 输出

echo 变量	输出字符串

print_r(变量)	输出每一个数据类型



var_dump(变量)	可以输出每一个数据类型，并且数据类型详细展示

```php
$arr = array(1,2,3,4,5);

echo $arr;
//输出 Array

print_r($arr);
//输出 Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 4 [4] => 5 )

var_dump($arr);
//输出 array(5) { [0]=> int(1) [1]=> int(2) [2]=> int(3) [3]=> int(4) [4]=> int(5) }

```



## 字符串

单引号是普通字符串

双引号可以解析字符串

```php
$num = 100;	//定义数字
echo "111$num";	//输出111100
echo '111$num';	//输出111$num
```

” + “只能数学运算，不可拼接字符串

” . “ 用来拼接字符串

```php
$num = '11' . '22';	//定义数字
echo $num;	//输出 1122
```



## if

和 js 类似

```php
$num = 1000;
if($num > 100){
    echo "$num > 100";
}else{
    echo "$num < 100";
}
```



## 循环

和 js 的 while 和 for 类似



## 数组

+ php 里没有 {} ,所以不可用 {} 来创建数组

+ 数组分两种，

   1. 索引型数组（等价于 js 的数组）

      ```php
      $arr = array(1,2,3,4,5);
      
      echo $arr;
      //输出 Array
      
      print_r($arr);
      //输出 Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 4 [4] => 5 )
      
      var_dump($arr);
      //输出 array(5) { [0]=> int(1) [1]=> int(2) [2]=> int(3) [3]=> int(4) [4]=> int(5) }
      ```

   2. 关联型数组（等价于 js 的对象）

      ```php
      	$arr = array('
      	name' => 'fs',
      	'age' => 18
      	);
      	
      	echo $arr;
      	//输出 Array
      	
      	print_r($arr);
      	//输出 Array ( [name] => fs [age] => 18 )
      	
      	var_dump($arr);
      	//输出 array(2) { ["name"]=> string(2) "fs" ["age"]=> int(18) }
      ```

+ 获取数组中的项

  ```php
  $arr = array(1,2,3,4,5);
  $arritem = $arr[4];
  
  $obj = array('name' => 'fs','age' => 18);
  $objitem = $obj['name'];
  var_dump($objitem);
  ```

  

## 导入语法

include

```php
include './test.php'
```



## die 强制结束

```php
die('链接失败，失败原因' . mysql_error());
```



## 操作浏览器的本地存储





## mysql

1. mysqli 和链接有关的类
2. msyqli_result 表达了对数据库查询所返回的结果集
3. musqli_stmt （重）



## 使用 php 操作数据库

1. 建立链接

   注意：有三种 `mysql_connext` , `mysqli_connext` , `PDO` 

   mysql_connect('主机名'，用户名‘，‘密码’)；

   ```php
   <?php
   	header('content-type:text/html;charset=utf-8;');
   	$sqlip = 'localhost';//主机名/ip
   	$sqluser = 'root';//数据库登录账号
   	$sqlpwd = 'admin';//数据库密码
   	$sqlname = 'test';//数据库名
   	
   
   	
   	//我的链接代码：用 mysql_connect 的面向对象方法链接
   	$conn = new mysqli($sqlip,$sqluser,$sqlpwd,$sqlname);
   	if(mysqli_connect_errno()){
   		echo '数据库连接错误';
   	}
   		echo '数据库连接成功';
   	var_dump($conn);
   	echo '--代码执行完毕--';
   
   
   
   	//参考链接代码(不建议使用)：用 mysql_connect
   	$con = mysql_connect($sqlip,$sqluser,$sqlpwd);
   	$select_db = mysql_select_db('test');
   	if (!$select_db) {
   	    die("could not connect to the db:\n" .  mysql_error());
   	}
   	//查询代码
   	$sql = "select * from user";
   	$res = mysql_query($sql);
   	if (!$res) {
   	    die("could get the res:\n" . mysql_error());
   	}
   	while ($row = mysql_fetch_assoc($res)) {
   	    print_r($row);
   	}
   	//查询代码
   	//关闭数据库连接
   	mysql_close($con);
   ?>
   ```

2. 查库

   mysqli_sqlqct_db()


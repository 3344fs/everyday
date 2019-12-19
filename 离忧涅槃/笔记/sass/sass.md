## 安装

npm i -g sass

## 检测

npm --version

## 转换

有几种编译模式

1. sass / scss 后缀的文件直接转换为 css 文件

   sass  要转换的文件名  要转成的文件名

   ```js
   sass index.sass indes.css
   ```

2. 实时编译（随着文件修改，实时修改编译文件，只能同时监控一个文件）

   sass  --watch  你要编译的文件(夹):你要生成的文件(夹)

   ```js
   sass --watch index.sass:index.css
   ```



## 注释

1. //

   在编译的时候不会保存

2. /* */

   编译时会保存，但在打包时会被清除

3. /*!  */

   打包时也会被保留

   

## 变量

+ 定义

  $变量名：值

  ```scss
  $bgc: #f99
  ```



## 嵌套

在一个规则集中可以直接写另一个规则集

+ 不加 >，后代选择器

    ```scss
    ul{
        width: 80%;
        margin: 10px auto;
        li{
            list-style: none;
        }
    }
    ```

+ 加 >，子代选择器

    ```scss
    ul{
        width: 80%;
        margin: 10px auto;
        > li{
            list-style: none;
        }
    }
    ```

+ & 链接伪类（不用&的话就会在中间产生一个空格）

  ```scss
  ul{
      &:hover{
          width: 80%;
  	    margin: 10px auto;
  	}
  }
  ```

+ 一个选择器嵌套多个 / 多个选择器嵌套一个

  ```scss
  div{
      width: 100px;
      box1, box2{
          width: 80%;
      }
  }
  ```

  ```scss
  box1, box2{
      width: 80%;
      p{
          color: #666;
      }
  }
  ```

+ 属性嵌套

  ```scss
  .test{
      width:0;
      height: 0;
      border: {
          top: 15px solid #f00;
          left: 15px solid #fff;
          right: 15px solid #fff;
          bottom: 15px solid #fff;
      }
  }
  ```

  ```scss
  .test{
      width:0;
      height: 0;
      border: 15px solid #fff{
          top: 15px solid #f00;
      }
  }
  ```

## 混入

混入混合器

+ 定义

  @mixin  函数名(){}

  注意：如果需要参数，那么传入的参数要用 `$` 修饰，在使用参数的时候也要用 `$` 

  ```scss
  @mixin tr($aa){
      transition: $aa 1s 0s;
  }
  ```

+ 使用函数

  @inclide  函数名

  ```scss
  div{
      @include tr;
  }
  ```
  
  带参数的混合器
  
  注意：如果需要参数，那么传入的参数要用 `$` 修饰，在使用参数的时候也要用 `$` ,没有默认值时，参数必须传够，否则会报错

  ```scss
@mixin tran($oldpx,$newpx){
      width: $oldpx;
    height: $oldpx;
      &:hover{
          width: $newpx;
          height: $newpx;
      }
  }
  ```
  
  形参设置默认值
  
  ```scss
  @mixin tran($w:100px,$h:500px,){
      width: $w;
      height: $h;
}
  ```
实参指定传值
  ```scss
  div{
      @include tran($h:200px);
  }
  ```



## 继承

+ @extend
  
    先继承其他元素的样式，再写自己的
    
    ```scss
    div{
        width: 100px;
        height: 100px;
        background-color: #f99;
        margin: 10px;
    }
    
    p {
     @extend div;
     margin: 50px;
    }
    ```



## 导入

@inport

一般情况下，一个文件专门定义变量，一个文件专门定义混合器

```scss
@inport './02.scss'
@inport './03.scss'
```


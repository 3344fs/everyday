参考文档：https://www.layui.com/doc/



## layer

弹出效果，使用方法：

1.引入 JQuery （1.8版本以上）

2.将下载包中的layer复制到项目中，并引入 layer 中的 layer.js

3.进入http://layer.layui.com/找到需要的类型

4.将代码复制到需要的 js 位置

例：

```html
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<meta http-equiv="X-UA-Compatible" content="ie=edge" />
	<script src="jquery-1.9.0.min.js"></script>
	<script src="layer/layer.js"></script>
	<title>Document</title>
	<script type="text/javascript">
		layer.open({
  type: 2,
  title: false,
  closeBtn: 0, //不显示关闭按钮
  shade: [0],
  area: ['340px', '215px'],
  offset: 'rb', //右下角弹出
  time: 2000, //2秒后自动关闭
  anim: 2,
  content: ['test/guodu.html', 'no'], //iframe的url，no代表不显示滚动条
  end: function(){ //此处用于演示
    layer.open({
      type: 2,
      title: '很多时候，我们想最大化看，比如像这个页面。',
      shadeClose: true,
      shade: false,
      maxmin: true, //开启最大化最小化按钮
      area: ['893px', '600px'],
      content: '//fly.layui.com/'
    });
  }
});
	</script>
</head>
<body>
</body>
</html>
```



## layDate

日期选择器，使用方法：

1.下载 laydate，地址：https://www.layui.com/laydate/

2.将下载包中的laydate复制到项目中，引入 laydate 中的 laydate.js

3.在需要的地方写就行

例：

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>使用 layDate 独立版</title>
</head>
<body>
<input type="text" id="test1">
<script src="laydate/laydate.js"></script> <!-- 改成你的路径 -->
<script>
//执行一个laydate实例
laydate.render({
  elem: '#test1' //指定元素
});
</script>
</body>
</html>
```

## layui

使用方法：

1.下载 layui，地址：https://www.layui.com/

2.将下载包中的layui复制到项目中，引入 layui 中的 layui.js

3.引入 layui/css 中的 layui.css
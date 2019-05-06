## [@font-face](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face)

引入字体文件，以达到自定义字体的目的。

最基本的用法是定义名称和指明资源路径（可以是存放在web服务器上的绝对路径或本机的相对路径）

如下代码：

``` html
<style>
		@font-face{
			font-family: "shoujinti";
			src:url("../font/font_shoujin.ttf"),
				url('https://github.com/LilyLaw/css-learning/blob/master/font/font_shoujin.ttf');
				
		}
		h1{
			font-family: "shoujinti";
		}
	</style>
	<h1>春江潮水连海平</h1>
```

这是最基本的用法，其他用法去看说明文档吧。
## margin 属性值按百分比的计算规则

### 普通元素的margin百分比
先看代码：
``` html
<style>
	.box{
		background: lightgreen;
		padding: 50px;
	}
	.con1{
		width: 400px;
		height: 200px;
		margin: 10%;
		background: blue;
		color: #fff;
	}
</style>
<div class="box">
	<div class="con1">
		帝高阳之苗裔兮，朕皇考曰伯庸。摄提贞于孟陬兮，惟庚寅吾以降。皇览揆余初度兮，肇锡余以嘉名。名余曰正则兮，字余曰灵均。纷吾既有此内美兮，又重之以修能。扈江离与辟芷兮，纫秋兰以为佩。汩余若将不及兮，恐年岁之不吾与。朝搴阰之木兰兮，夕揽洲之宿莽。日月忽其不淹兮，春与秋其代序。惟草木之零落兮，恐美人之迟暮。
	</div>
</div>
```
演示结果会让人意想不到：

![margin百分比](https://github.com/LilyLaw/css-learning/blob/master/img/margin百分比.png?raw=true)

``` scss
margin: 10%;
```
这个10%是按照`父元素宽度`来算的，即使在高度上也是10%，但取值是`父元素元素宽度×10%` 一定要注意这一点。
还要注意一点：如果父元素设置了`padding`属性，则取值为`（父元素宽度-父元素左padding-父元素右padding）×10%` ，**注意padding要减去**

### 绝对定位元素的margin百分比

``` html
<style>
	.box{
		background: lightgreen;
		height: 600px;
		position: relative;
	}
	.father{
		width: 800px;
		height: 500px;
		background: pink;
	}
	.con1{
		width: 400px;
		height: 200px;
		margin: 10%;
		background: blue;
		color: #fff;

		position: absolute;
	}
</style>
<div class="box">
	<div class="father">
    	<div class="con1">
    		帝高阳之苗裔兮，朕皇考曰伯庸。摄提贞于孟陬兮，惟庚寅吾以降。皇览揆余初度兮，肇锡余以嘉名。名余曰正则兮，字余曰灵均。纷吾既有此内美兮，又重之以修能。扈江离与辟芷兮，纫秋兰以为佩。汩余若将不及兮，恐年岁之不吾与。朝搴阰之木兰兮，夕揽洲之宿莽。日月忽其不淹兮，春与秋其代序。惟草木之零落兮，恐美人之迟暮。
    	</div>
	</div>
</div>
```
看下效果：

下图是绝对定位元素的第一个带有定位属性的祖先元素宽度：

![绝对定位元素的带有定位属性的祖先元素宽度](https://github.com/LilyLaw/css-learning/blob/master/img/margin绝对定位1.png?raw=true)

定位元素的margin：

![绝对定位元素margin](https://github.com/LilyLaw/css-learning/blob/master/img/绝对定位元素margin.png?raw=true)

所以绝对定位元素的margin 百分比是按照第一个带有定位（relative，absolute，fixed）的祖先元素的宽度计算的。

### margin百分比应用场景

可以简单实现一个宽高比为2:1的矩形。
``` html
<style>
	.box{
		background: lightgreen;
		overflow: hidden;
	}
	.father{
		margin: 50%;
	}
</style>
<div class="box">
	<div class="father">
	</div>
</div>
```
在浏览器就会看到，`class="box"` 的元素宽高比永远是2:1，这里涉及到margin重叠，可能比较难理解。






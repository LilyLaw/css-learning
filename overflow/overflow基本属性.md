## overflow基本属性

visible，hidden，scroll就不说了，自己查去。

### overflow：auto

如果x轴方向超出，则x方向出现滚动条，可滚动。y轴同理

### overflow-x：hidden 和 overflow-y：hidden

``` html
<style>
	.div1{
		width: 600px;
		height: 600px;
		background: lightgreen;
		overflow-y:hidden;
	}
</style>
<div class="div1">
	<img src="2.jpg" alt="">
</div>
```

假设图片宽800px，高700px，div1设置了overflow-y：hidden之后，y方向高度不够，被隐藏掉了，而x方向宽度不够，却自己加上了一个滚动条。

>如果overflow-x和overflow-y属性值相同，则等同与overflow；

>如果overflow-x和overflow-y属性值不同，且其中一个被赋予visible，另外一个被赋予hidden，scroll，auto，那么这个visible会被重置为auto。

这就是为什么水平方向会出现滚动条的原因。

### overflow属性起作用的前提

1. display 非 inlin水平。
	比如你给一个span标签设置overflow是不起作用的
2. 设置尺寸限制，比如设置width，height，max-width，max-height或绝对定位拉伸。
3. 对于td元素，要对table设置table-layout：fixed；如下代码：
``` html
<style>
	table{
		width: 50px;
		background: lightgreen;
		table-layout:fixed;
	}
	td{
		overflow: hidden;
	}
</style>
<table class="mytable">
	<tbody>
		<tr>
			<td>title</td>
			<td>title</td>
			<td>title</td>
		</tr>
	</tbody>
</table>
```


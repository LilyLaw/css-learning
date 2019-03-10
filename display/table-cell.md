## display:table-cell

display:table-cell属性指让标签元素以表格单元格的形式呈现，类似于td标签。
所以这个属性应用于某些场景。
比如下面这个例子，让元素水平且垂直居中：
``` htm
<style>
		.box{
			width: 300px;
			height: 200px;
			background: lightgreen;
			display: table-cell;
			vertical-align: middle;
			text-align: center;
		}
	</style>
	<div class="box">
		<div class="con">box</div>
	</div>

	<div class="box">
		<div class="con">box1111</div>
	</div>
```

这个例子是比较常用的，张鑫旭大神还总结了其他的用法https://www.zhangxinxu.com/wordpress/2010/10/%E6%88%91%E6%89%80%E7%9F%A5%E9%81%93%E7%9A%84%E5%87%A0%E7%A7%8Ddisplaytable-cell%E7%9A%84%E5%BA%94%E7%94%A8/
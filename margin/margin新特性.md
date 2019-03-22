## margin新特性

下面介绍的新特性，浏览器兼容方面不是很好，目前只webkit内核兼容,谨慎使用.
 
 ### margin-start
 
 margin-start 默认情况下等价于margin-left（不叠加，两者共存默认取margin-left）如果加上writing-mode的话，则按writing-mode方向的margin-left计算
 
``` html
div{
		width: 100px;
		height: 100px;
	}
	.div1{
		background: pink;
		margin-bottom: 50px;
	}
	.div2{
		-webkit-margin-start:100px;
		margin-left: 300px;
		margin-top: 50px;
		background: lightgreen;
	}
</style>
<div class="div1">1</div>
<div class="div2">2</div>
```
同理，可知 ```margin-end``` 
 
### margin-block-start

margin-block-start 默认是文档流起始方向

所以默认情况下，margin-block-start 属性等价于 margin-top （不叠加，两者都存在的话取margin-block-start）如果加上writing-mode的话，则按writing-mode方向计算
``` html
<style>
	div{
		width: 100px;
		height: 100px;
		background: lightgreen;
		float: left;
	}
	.div2{
		margin-top: 100px;
		margin-block-start:200px;
	}
</style>
<div class="div1">1</div>
<div class="div2">2</div>
```

同理，可知 ```margin-block-end```

### margin-collapse

margin-collapse主要针对margin重叠，默认值是collapse（重叠）

不处理margin重叠：
``` html
<style>
	div{
		width: 100px;
		height: 100px;
	}
	.div1{
		background: pink;
		margin-bottom: 50px;
	}
	.div2{
		margin-top: 50px;
		background: lightgreen;
	}
</style>
<div class="div1">1</div>
<div class="div2">2</div>
```

设置margin-collapse：separate，使margin不重叠
``` stylus
.div2{
	-webkit-margin-collapse:separate;
	margin-top: 50px;
	background: lightgreen;
}
```

设置margin-collapse：discard，取消所有margin值（发生重叠的方向）
``` stylus
.div2{
	-webkit-margin-collapse:discard;
	margin-top: 50px;
	background: lightgreen;
}
```

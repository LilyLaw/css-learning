## [z-index](https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index)

先看一下官方文档介绍：
> z-index 属性指定了一个具有定位属性的元素及其子代元素的 z-order。 当元素之间重叠的时候，z-order 决定哪一个元素覆盖在其余元素的上方显示。 通常来说 z-index 较大的元素会覆盖较小的一个。

我翻译一下：元素有定位，z-index值越大越叠在上面。

我们先看一下没有定位的正常文档流里层级顺序：
``` html
<style>
	div{
		width: 100px;
		height: 100px;
		font-size: 30px;
		font-weight: bold;
	}
	.div1{
		background: green;
	}
	.div2{
		background: yellow;
		margin-top: -50px;
	}
</style>
<div class="div1">1</div>
<div class="div2">2</div>
```
渲染效果：

![正常文档流层叠顺序](https://github.com/LilyLaw/css-learning/blob/master/img/normalzindex.png?raw=true)

我们可以看到，后面的元素会覆盖前面的。这是在没有定位的正常文档流中元素的层级顺序。

然而加了position定位，但没有任何top、left、right、bottom修饰时会怎样呢？
如果是relative，那么肯定没有任何效果，所有元素在没有任何top之类修饰的时候会按照普通文档流去渲染，不会重叠。而如果是absolute，则会重叠，然后z-index最大的覆其次，以此类推。

思考了position以后，思考一段代码
``` html
<style>
	div{
		font-size: 30px;
		font-weight: bold;
	}
	.div1{
		background: green;
		position: absolute;
		z-index: 5;
		width: 400px;
		height: 400px;
		top: 0;
		left: 100px;
	}
	.div2{
		background: yellow;
		position: absolute;
		z-index: 10;
		width: 300px;
		height: 300px;
		top: 100px;
		left: 200px;
	}
	.sondiv2{
		background: blue;
		position: absolute;
		z-index: 2;
		width: 100px;
		height: 100px;
		top: 100px;
		left: 100px;
	}
</style>
<div class="div1">1</div>
<div class="div2">
	father
	<div class="sondiv2">son</div>
</div>
```
渲染效果：

![enter description here](https://github.com/LilyLaw/css-learning/blob/master/img/zindexfather.png?raw=true)

由此可见，元素的z-index值受父元素影响：如果父元素层级比别的大，那么无论子元素层级多小都会覆盖其他。

如果父元素小于其他元素层级，而子元素大于其他层级呢？看下面代码：
``` html
<style>
	div{
		font-size: 30px;
		font-weight: bold;
	}
	.div1{
		background: green;
		position: absolute;
		z-index: 10;
		width: 400px;
		height: 400px;
		top: 0;
		left: 100px;
	}
	.div2{
		background: yellow;
		position: absolute;
		z-index: 5;
		width: 300px;
		height: 300px;
		top: 100px;
		left: 200px;
	}
	.sondiv2{
		background: blue;
		position: absolute;
		z-index: 20;
		width: 100px;
		height: 100px;
		top: 100px;
		left: 100px;
	}
</style>
<div class="div1">1</div>
<div class="div2">
	father
	<div class="sondiv2">son</div>
</div>
```
效果跟我想的不一样：

![enter description here](https://github.com/LilyLaw/css-learning/blob/master/img/zindex2.png?raw=true)

我以为z-index值最大的会在上面，然而并不。所以得出结论，子元素无法脱离父元素：父元素层级大则子元素可以显示；父元素层级小，子元素层级再大也没用。

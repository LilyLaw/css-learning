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


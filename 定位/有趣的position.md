## [position][1]

### relative

官方文档如下解释
> 元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。position:relative 对 table-*-group, table-row, table-column, table-cell, table-caption 元素无效。

我自己理解的意思是：以未添加定位时渲染的位置为基准，通过 top 、left 、right 、bottom 来控制元素的位置，同时在原位置预留空白。如果位置重叠，后写的元素会覆盖先写的元素。具体看下代码：
``` html
<style>
	.div1{
		  width: 100px;
		  height: 100px;
		  background: green;

		  position: relative;
		  top: 100px;
		  left: 100px;
	}
</style>
<div class="div1"></div>
```
此时观察网页布局：

![relative][2]

```<body``` 的高度是100，但body内部唯一的元素位置却在高度100之外。说明position：relative 的元素即使通过定位移到了其他位置，但文档仍会在原位置（即未添加定位的位置）为其预留出空间。

看下面的两端代码，在浏览器查看渲染效果，思考，就会更能体会`以原位置为基准进行定位`这句话的意思.

代码段1：
``` html
<style>
	*{  margin: 0;  padding: 0;}
	.div1{
	  width: 100px;
	  height: 100px;
	  background: green;

	  position: relative;
	  top: 100px;
	  left: 100px;
	}

	.div2{
	  width: 100px;
	  height: 100px;
	  background: red;

	  position: relative;
	  top: -100px;
	  left: 80px;
	}
</style>
<div class="div1"></div>
<div class="div2">2</div>
```

代码段2：
``` html
<style>
	*{
	  margin: 0;
	  padding: 0;
	}
	.div1{
	  width: 100px;
	  height: 100px;
	  background: green;

	  position: relative;
	  right: 50px;
	  bottom: 50px;
	}
</style>
<div class="div1"></div>
```

### absolute
官方解释：
> 不为元素预留空间，通过指定元素相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。

ok，官方解释很易懂，我们直接看下面一段代码，感受一下absolute和relative的不同：
``` html
<style>
	*{
	  margin: 0;
	  padding: 0;
	}
	.div1{
	  width: 100px;
	  height: 100px;
	  background: green;

	  position: absolute;
	}
</style>
<div class="div1"></div>
```
浏览器查看一下效果：

![absolute][3]

此时```<div class="div1"></div>``` 这个元素的宽高都有，但body和html的高度都是0，说明position：absolute定位的元素已经脱离的文档流，文档不会在其原位置预留空白。这是absolute的一个特定，也是与relative不同的地方。

下面再看2个例子，看看定位与正常混用的效果：
``` html
<style>
    *{
      margin: 0;
      padding: 0;
    }
    .div1{
      width: 100px;
      height: 100px;
      background: green;

      position: absolute;
    }
    .div2{
      width: 100px;
      height: 100px;
      background: red;
    }
</style>
<!--div1定位在前，脱离文档流，div2 正常渲染，但被div1覆盖了-->
<div class="div1"></div>
<div class="div2"></div>
```
第二个
``` html
<style>
	*{
	  margin: 0;
	  padding: 0;
	}
	.div1{
	  width: 100px;
	  height: 100px;
	  background: green;

	  position: absolute;
	}
	.div2{
	  width: 100px;
	  height: 100px;
	  background: red;
}
</style>
<div class="div2"></div>
<div class="div1"></div>
```
第二个渲染如下：

![absolute][4]

我看别人的解释是，定位的元素在后面，因为没有给定位的元素设置top，left的值，所以按照顺序往下渲染。

关于absolute的top，left，right，bottom和relative都不尽相同，同时也跟他父元素的定位有关，自行体会。

### fixed
相对窗口定位，跟父元素什么的无关，没啥好说的。

### inherit
继承父元素的position属性，这也没啥可说的。



  [1]: https://developer.mozilla.org/zh-CN/docs/Web/CSS/position
  [2]: https://github.com/LilyLaw/css-learning/blob/master/img/relative.bmp?raw=true
  [3]: https://github.com/LilyLaw/css-learning/blob/master/img/absolute1.bmp?raw=true
  [4]: https://github.com/LilyLaw/css-learning/blob/master/img/absolute2.bmp?raw=true
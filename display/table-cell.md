## display:table-cell

display:table-cell属性指让标签元素以表格单元格的形式呈现，类似于td标签。
所以这个属性应用于某些场景。
### 让元素水平且垂直居中：
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

### 经典的一栏固定，一栏宽度自适应的布局

``` html
<style>
  .all{
	width: 100%;
	background: lightgreen;
  }
  .box{
	width: 80%;
	background: pink;
	margin: auto;
  }
  .img{
	width: 250px;
	height: auto;
	float: left;
  }
  .img img{
	width: 100%;
	height: auto;
  }
  .con{
	display: table-cell;
  }
</style>
<div class="all">
	<div class="box">
	  <div class="img">
		<img src="./1.jpg" alt="">
	  </div>
	  <div class="con">
		原因在于：IE6/7下block属性的元素对inline-block属性是有反应，但是却不是纯洁的反应，而是怪蜀黍看到粉嫩小萝莉的一点邪念，就是让元素有个怪异的haslayout属性。//zxx:大家似乎都喜欢用haslayout解析一些老IE下的一些怪异现象，但我自己打心底里是不认同这个概念。如果IE6/7是很标准的纯洁的解释inline-block属性的话，是无法实现自适应的，右侧的文字描述内容会跑到头像的下面，哦呵呵~~有点负负得正，以毒攻毒的意味。代码如下：display:table-cell; *display:inline-block;就万事大吉，收工回家了。在本例demo中，右侧内容足够多，所以宽度完整的撑开了，如果内容有限，则宽度就是内容的宽度，此时想要让某个元素（例如关闭按钮）右侧定位就会有问题，解决方法就是定义一个非常宽的宽度，就像上面facebook截图中的CSS属性一样，所以，考虑到各种情况，更健壮耐用的CSS代码应如下：display:table-cell;*display:inline-block;width:2000px; *width:auto;或者使用：display:table-cell;  width:2000px; *width:auto; *zoom:1;这种两栏的自适应布局，不仅不要分别丈量与计算两列的宽度，连“页面重构鑫三无准则之无宽度准则”中absolute自适应布局的头像宽度都不需要亮了，可以说是更加懒惰，更加直接的好方法。三、display:table-cell下的等高布局
	  </div>
	</div>
</div>
```
一般实现上述效果，除了左浮动意外，con这个元素要margin-left才可以，但此处使用display:table-cell 就可以实现。

### 等高布局

这块儿是我写的代码，但完全不起效果，不知道哪里除了问题。。。
``` html
<style>
  .all{
	width: 1000px;
	background: lightgreen;
  }
  .box{
	display: table-row;
	overflow: hidden;
  }
  .list{
	display: table-cell;
	width: 30%;
  }
</style>
<div class="all">
	<div class="box">
	  <div class="list">111</div>
	  <div class="list">2222222222222222222222222222222222222222222222222222222222</div>
	  <div class="list">333</div>
	</div>
</div>
```
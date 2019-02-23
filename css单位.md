# [css 单位][1]

## 相对长度单位

> 相对长度代表着以其它距离为单位的一种尺寸。使用这个单位的，可以是指定字符的大小，行高，或者是viewport的大小。

### em（用的比较多）
先看代码：
css部分
``` stylus
p{
  font-size: 20px;
}
span{
  font-size: 2em;
}

div{
  font-size: 2em;
}
```
html部分
``` html
<body>
  <p> I wish I had done <span>everything</span> on earth with you </p>

  <div>the good earth</div>
</body>
```

如果父元素有font-size 属性，比如上例中的p元素 font-size属性值是20px。那p元素的子元素中每 ```1em``` = ```20px```。 即子元素的em标准来源于父元素。

那么问题来了，如果一个元素没有父元素，此元素的em取值是多少呢？如上例中的div元素。
查了资料最后得出结论，它会一直向上追溯，直到追溯到body元素。如果body没有设置font-size，则根据浏览器的默认设置来取值。

### ex
在含有“X”字母的字体中，它是该字体的小写字母的高度；对于很多字体， 1ex ≈ 0.5em。
如下代码：

``` html
<style>
	.xheight{
	  width: 300px;
	  height: 1ex;
	  background: green;
	}
</style>
<h1>定义一条与字母x高度相同的线：</h1>
<div>xxxxxxxxxxxXXXXX</div> 
<div class="xheight"></div>
```
我自己也看了一下，发现它高度不是很直观，好像是有点短，就是1ex< x的高度。自己感觉，希望是我感觉出错。**所以这个单位有啥特殊的用处么？？？**

### ch
1ch = 数字“0”的宽度如下代码：
``` html
  <div style="width: 10ch;overflow: hidden;">0000000000000000000000000000000</div>
```
**所以这个单位有啥特殊的用处么？？？**

### rem（用的比较多）
根元素的font-size。根元素就是```<html>```
如下代码：
``` html
<style>
	html{
	  font-size: 50px;
	}
	div{
	  font-size: 1rem;
	}
</style>
<div>devil or angel</div>
```

### lh
等于元素行高line-height的计算值，搜了半天也没搜到啥资料，应该用的不多。

### vw
视口宽度的1/100；

### vh
视口高度的1/100；

### vmin
视口高度和宽度之间的最小值的 1/100。

### vmax
视口高度和宽度之间的最大值的 1/100。

**vw，vh 用的比较多，尤其是移动端**
代码如下，自行感受：
``` html
<style>
	div{
	  font-size: 5vw;
	}
	p{
	  font-size: 5vh;
	}
	section{
	  font-size: 5vmin;
	}
	article{
	  font-size: 5vmax;
	}
</style>
<div>devil or angel</div>
<p>devil or angel</p>
<section>devil or angel</section>
<article>devil or angel</article>
```

## 绝对长度单位

### px
与显示设备相关。
对于屏幕显示，通常是一个设备像素（点）的显示。
对于打印机和高分辨率的屏幕，一个CSS像素意味着多个设备像素，因此，每英寸的像素的数量保持在96左右。
具体的看一下这个文档 http://www.mamicode.com/info-detail-2396539.html

其他的绝对长度单位用的不多，知道就行。 


  [1]: https://developer.mozilla.org/zh-CN/docs/Web/CSS/length
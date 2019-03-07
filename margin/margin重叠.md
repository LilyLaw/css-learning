## margin 重叠

margin重叠一般值margin-top 或 margin-bottom重叠。在不考虑write-mode的方式下，只探讨margin-top 和 margin-bottom。

### 相邻元素重叠
``` html
<style>
	p{
		line-height: 2em;
		font-size: 1em;
		background: lightgreen;
		margin: 1em 0;
	}
</style>
<p>111</p>
<p>222</p>
```
看一下演示效果：

![相邻元素重叠](https://github.com/LilyLaw/css-learning/blob/master/img/相邻元素重叠.png?raw=true)

可以看到，两个`<p>`之间的距离只有1em，这是因为第一个元素的margin-bottom和第二个元素的margin-top重叠到一起了。

### 父级和第一个/最后一个子元素重叠

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
    	.box{
    		background: lightgreen;
    		height: 100px;
    	}
    	.son{
    		margin-top: 50px;
    		border: 1px solid red;
    	}
    </style>
</head>
<body>
    <div class="box">
    	<div class="son">
    		son
    	</div>
    </div>
</body>
</html>
```
按常理，`class="son"`这个盒子上面应该有50像素的浅绿色父元素背景，但演示效果如下：

![margin重叠父子元素](https://github.com/LilyLaw/css-learning/blob/master/img/margin重叠父子元素1.png?raw=true)

可以看到**父元素和第一个子元素的margin-top重叠在了一起**。

再看一段代码：
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
    	.box{
    		background: lightgreen;
    	}
    	.son{
    		margin-bottom: 50px;
    		border: 1px solid red;
    	}
    </style>
</head>
<body>
    <div class="box">
    	<div class="son">
    		son
    	</div>
    	<div class="son">
    		son
    	</div>
    	<div class="son">
    		son
    	</div>
    </div>
</body>
</html>
```
效果如下：

![margin父子元素重叠](https://github.com/LilyLaw/css-learning/blob/master/img/margin父子元素重叠2.png?raw=true)

父元素和最后一个子元素的margin-bottom重叠了。

总结一下，父子元素margin重叠的条件是什么呢？

#### 若要margin-top重叠
1. 父元素没有`border-top`属性
2. 父元素和第一个子元素之间没有内联元素：比如文字，图片等等。
3. 父元素没有padding-top属性，或者padding-top属性值为0；
4. **父元素非块状格式化元素** （这块儿没懂。。。）

### 若要margin-bottom重叠
前四条同上，只不过针对bottom和最后一个元素。再加一条 5. 父元素没有height，min-height，max-height的限制。（**这里有争议，待考量**）




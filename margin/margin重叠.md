## margin 重叠

margin重叠一般值margin-top 或 margin-bottom重叠。在不考虑write-mode（一般文字从左到右，或者从右到左，都是横着排列。但也有从上到下写字的，不考虑从上到下这种模式）的方式下，只探讨margin-top 和 margin-bottom。

### 一、相邻元素重叠
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

### 二、父级和第一个/最后一个子元素重叠

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

#### 若要margin-bottom重叠
前四条同上，只不过针对bottom和最后一个元素。再加一条
5.父元素没有height，min-height的限制。（**这里有争议，待考量**）

### 三、空block元素margin重叠

``` html
<style>
	.father{
		background: lightgreen;
		overflow: hidden;
	}
	.son{
		margin: 50%;
	}
</style>
<div class="father">
	<div class="son">
	</div>
</div>
```
解释一下：父元素`<div class="father">`没有高度和宽度，所以靠子元素撑起来。
子元素margin的上下左右都是50% ，但子元素左右margin不重叠，上下margin重叠，因此father这个盒子的宽高比就是2:1 。父元素只是展示一下效果，他本身没有重叠，发生margin重叠的是子元素son的margin-top和margin-bottom 。

#### 若要空block元素margin重叠需满足以下条件
1. 元素没有border-top且没有border-bottom
2. 元素没有padding-top且没有padding-bottom，或者padding-top为0且padding-bottom为0；
3. 元素内没有内联元素
4. 没有height和min-height属性，或者height和min-height均为0；

空block元素重叠可以有这样一个特殊应用：<font color="red">**做一个宽高比永远等于2:1的盒子，随屏幕宽度自适应**</font>

### 四、margin重叠计算规则

1. 正正取最大值
    ``` html
    <style>
        div{
            width: 200px;
            height: 100px;
            background: lightgreen;
        }
        .sib1{
            margin-bottom: 20px;
        }
        .sib2{
            margin-top: 100px;
        }
    </style>
    <div class="sib1">1</div>
    <div class="sib2">2</div>
    ```
看下演示效果：
整个body里只有两个元素，body被撑起来后高度是300px
 ![body](https://github.com/LilyLaw/css-learning/blob/master/img/body.png?raw=true)

sib1这个盒子margin-bottom是20px

![sib1](https://github.com/LilyLaw/css-learning/blob/master/img/sib1.png?raw=true)

sib2这个盒子margin-top是100px，从下图我们可以看到，sib1的margin-bottom和sib2的margin-top重叠了，取两个最大值：

![sib2](https://github.com/LilyLaw/css-learning/blob/master/img/sib2.png?raw=true)

以此类推：父子重叠、空block元素重叠也是一样的，都是正数取最大值。

2. 正负相加
意思就是如果margin-top和margin-bottom中有一个是正数（比如50px），有一个是负数（比如-30px），则最终取值正数加负数（50px + -30px = 20px）。不举例子了，自己测试去吧。

3. 负负取绝对值大的负数。
取绝对值最大的负数，不举例子了，自己练去吧。

### 五、margin重叠的意义和良好应用

在设计最初，不同元素的默认margin不同，不同标签混合时margin无规律，排版不规律。
网页设计有这样两种现象：
1.网页中任何地方插入裸div不会影响原来布局（裸div就是没有任何css修饰的，里面也没有任何实质性内容的div）
2. 页面中插入多个空的`<p>` ,不会影响原来阅读排版。多个p元素margin重叠最后只看到一个p元素的位置

margin重叠比较好的应用：
表单列表项，很简单的例子，只阐述margin的效果：
``` html
<style>
    ul{
        background: lightgreen;
        overflow: hidden;
    }
    li{
        list-style: none;
        margin-top: 20px;
        margin-bottom: 20px;
    }
</style>
<form action="">
    <ul>
        <li>name:<input type="text"></li>
        <li>age:<input type="text"></li>
        <li>sex:<input type="text"></li>
        <li>grade<input type="text"></li>
        <li>school<input type="text"></li>
        <li><input type="submit"></li>
    </ul>
</form>
```
一般我们要实现上述效果会给每一个li设置一个margin-top，然后给最后一个li设置一个margin-bottom。但这样存在一个问题：若把最后一个li删掉，则margin-bottom就没有了，页面布局就会乱掉。

而向上述代码写法无论怎么删除都不会影响整体布局效果，程序比较健壮，利于后期维护。这是margin重叠非常巧妙的一个用处。



## margin 深度理解

### margin 对容器尺寸的影响

先了解盒子模型，之后看下面代码

``` html
<style>
    .box{
    	background: lightgreen;
    	padding: 50px;
    	margin-bottom: 50px;
    	color: #fff;
    	font-size: 18px;
    	font-weight: bold;
    }
    .con1{
    	background: green;
    	margin: 20px 30px;
    }
    
    .con2{
    	background: green;
    	margin: 50px 100px;
    }
</style>
<div class="box">
    <div class="con1">
    	<p>111</p>
    	<p>111</p>
    </div>
    </div>
    
    <div class="box">
    <div class="con2">
    	<p>222</p>
    	<p>222</p>
    </div>
</div>
```
演示效果如下

![margin](https://github.com/LilyLaw/css-learning/blob/master/img/margin.png?raw=true)

我自己测试发现，margin对于元素宽度会影响，但对于高度无影响。

这个特性很神奇，那么它有什么特殊的作用吗？
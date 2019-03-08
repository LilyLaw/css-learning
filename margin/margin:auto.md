## margin:auto

### 1. margin:auto作用机制：
1. 如果margin-left和margin-right都是auto，如：`div{margin:20px auto}`, 则左右平分剩余空间
    ``` html
    <style>
        .box{
            background: lightgreen;
            color: #fff;
            width: 100%;
            overflow: hidden;   /* 防止父子元素margin重叠 */
        }
        .con{
            background: orange;
            margin: 50px auto;
            width: 600px;
        }
    </style>
    <div class="box">
        <div class="con">margin:auto</div>
    </div>
    ```
2. 如果margin-left或margin-right一方是固定值，一方是auto，则固定值一方占据固定空间，auto一方占据剩余空间
    ``` html
    <style>
        .box{
            background: lightgreen;
            color: #fff;
            width: 100%;
            overflow: hidden;   /* 防止父子元素margin重叠 */
        }
        .con{
            background: orange;
            margin: 50px 100px 50px auto;
            width: 600px;
        }
    </style>
    <div class="box">
        <div class="con">margin:auto</div>
    </div>
    ```

### 二、关于margin:auto 无法垂直居中的问题
先看代码：
``` html
<style>
    .box{
        background: lightgreen;
        width: 100%;
        height: 600px;
        overflow: hidden;   /* 防止父子元素margin重叠 */
    }
    .con{
        background: orange;
        margin: auto;
        width: 300px;
        height: 300px;
    }
</style>    
<div class="box">
    <div class="con">margin:auto</div>
</div>
```
演示效果可见class="con" 这个div元素只实现了水平居中，没有垂直居中

<font color="red" size=5>**为啥margin:auto不能垂直居中呢？？？**</font>

答曰：父元素高度固定，宽度固定，块级子元素如果有内容且不加任何css修饰，它的宽度会默认占满父元素的宽度，比如下面这样：
``` html
<div class="box">
    <div class="con">这是子元素的内容</div>
</div>
```
但是<font color="red">**子元素高度是不会占满父元素高度的！！！**</font>，所以做不到垂直居中。
这样理解可能有点牵强。。。换个角度，父元素如果有多个子元素，假设高度都垂直居中，且都是块级元素不能排成一排，那岂不是所有子元素都重叠了么？而宽度居中则不会影响，会在父元素中间位置排成一列。这样就好理解了，margin:auto不能实现垂直居中。
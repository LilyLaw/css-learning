## CSS3 [animation][1]

animation 属性是一个简写属性，用于设置八个动画属性：
- animation-name  指定应用的一系列动画，每个名称代表一个由@keyframes定义的动画序列
- animation-duration  规定完成动画所花费的时间，以秒或毫秒计,指定一个动画周期的时长。
- animation-timing-function  规定动画的速度曲线。
- animation-delay  规定在动画开始之前的延迟。
- animation-iteration-count  规定动画应该播放的次数。
- animation-direction  规定是否应该轮流反向播放动画。
- animation-fill-mode: 指定在动画执行之前和之后如何给动画的目标应用样式。
- animation-play-state: 定义一个动画是否运行或者暂停。可以通过查询它来确定动画是否正在运行。另外，它的值可以被设置为暂停和恢复的动画的重放。

看代码：
``` html
<!DOCTYPE html>
<html lang="cn">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
  <meta name="format-detection" content="telephone=no">
  <meta http-equid=“X-UA-Compatible” content=“IE=edge, chrome=1”>
  <title>正方体</title>
  <style>
    html{
        height: 100%;

        background: -webkit-radial-gradient(center, ellipse, #430d6d 0%, #000 100%);
        background: radial-gradient(ellipse at center, #430d6d 0%, #000 100%);
    }

    #window{
        position: absolute;
        top: 50%;
        left: 50%;

        width: 20em;
        height: 20em;
        margin-top: -10em;
        margin-left: -10em;

        -webkit-perspective: 1500px;
    }

    #box{
        position: absolute;

        width: 100%;
        height: 100%;

        -webkit-transform: rotateX(-20deg) rotateY(-20deg);
        -webkit-animation: 6s spin linear infinite both;

        -webkit-transform-style: preserve-3d;
        transform-style: preserve-3d;
    }

    .face{
        position: absolute;
        width: 100%;
        height: 100%;

        color: #77ffb9;
        background: -webkit-linear-gradient(left, rgba(54, 226, 248, .5) 0px, rgba(54, 226, 248, .5) 3px, rgba(0, 0, 0, 0) 0px), 
                    -webkit-linear-gradient(top, rgba(54, 226, 248, .5) 0px, rgba(54, 226, 248, .5) 3px, rgba(0, 0, 0, 0) 0px);
        background-color: rgba(0, 0, 0, .5);
        -webkit-background-size: 2.5em 2.5em;
        box-shadow: inset 0 0 5em rgba(125, 125, 125, .8);
    }

    #face-front{
        transform: translateZ(10em);
    }

    #face-left{
        -webkit-transform: rotateY(-90deg) translateZ(10em);
    }

    #face-top{
        -webkit-transform: rotateX(90deg) translateZ(10em);
    }

    #face-right{
        -webkit-transform: rotateY(90deg) translateZ(10em);
    }

    #face-bottom{
        -webkit-transform: rotateX(-90deg) translateZ(10em);
    }

    #face-back{
        -webkit-transform: rotateX(180deg) translateZ(10em);
    }


    @-webkit-keyframes spin{
        from
        {
            -webkit-transform: translateZ(-10em) rotateX(0) rotateY(0deg);
            transform: translateZ(-10em) rotateX(0) rotateY(0deg);
        }

        to
        {
            -webkit-transform: translateZ(-10em) rotateX(360deg) rotateY(360deg);
            transform: translateZ(-10em) rotateX(360deg) rotateY(360deg);
        }
    }

  </style>
</head>
<body>
    <div id="window">
          <div id="box">
                <div class="face" id="face-front">1</div>
                <div class="face hide" id="face-left">2</div>
                <div class="face hide" id="face-top">3</div>
                <div class="face hide" id="face-right">4</div>
                <div class="face hide" id="face-bottom">5</div>
                <div class="face hide" id="face-back">6</div>
          </div>
    </div>

    X:<input id="changex" type="range" name="" min="-100" max="100" onchange="ratate()"/>
    <br>
    Y:<input id="changey" type="range" name="" min="-100" max="100" onmousemove="ratate()"/>

    <script>
     function ratate()
      {
        var x = document.getElementById('changex').value;
     var y = document.getElementById('changey').value;
     document.getElementById('window').style.webkitPerspectiveOrigin = x+"% "+y+"%";
     }
    </script>
</body>
</html>
```


  [1]: https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation
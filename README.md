# bootstrap
这是bootstrap的综合实战，涉及了bootstrap的常用组件以及使用了外部插件，同时也在添加标签页面使用h5的localstorage进行倒动态存储添加的标签
这个访问[地址](https://chenjiaobin.github.io/bootstrap/index.html)和二维码
![扫一扫进入网站](https://raw.githubusercontent.com/chenjiaobin/bootstrap/master/img/1515042989.png)
# wow和animaate的应用
首先需要在页面上引入对应的文件animage.css文件和wow.min.js文件,这两个文件是必不可少的，当然还需要jquery.min.js,引入这两个文件后就可以在页面上使用了
animate.css的方法[参考网址](https://daneden.github.io/animate.css/)这里面有各种过渡方法，直接用，加在你的class上面
```
//在外层div上加上wow（必不可少） 和 animate的方法(比如fadeInUp,fadeInDown....)
<div class="row wow fadeInUp" data-wow-duration="1s" data-wow-delay="1s">
  <div class="col-md-1"></div>
  <div class="col-md-10">
    <h1>Bootstrap的联系</h1>
    <p>这是来自于demo的模仿<br>这是文本2</p>
    <img src="img/php.jpg" class="img-responsive" alt="php">
  </div>
  <div class="col-md-1"></div>
</div>
<script>
// 初始化
new WOW().init();
</script>
```
animate插件给使用对象添加`class="wow+animate"(animate是写他的方法，而不是写这个animate)`
它的其他可用属性有`data-wow-duration='1s' 过渡执行时间`和`data-wow-delay='2s' 延迟设置`和`data-wow-offset='10' 设置偏移量`和`data-wow-iteration="10" 过渡重复次数`
整体呈现的效果是，当你鼠标滚动的时候，在你有设置的区域会有一个过渡的效果呈现
# singlePageNav的应用
这个插件的主要作用是在当前页面上跳转，就是通过设置锚点跳转以及js初始化就可以呈现点击锚点过渡跳到锚点连接的位置，也可以设置偏移量(一般这个偏移量主要是当你的顶部导航设置成固定的时候就需要用到，偏移的量就是你的顶部导航的高度，这样页面就不会被你的导航覆盖)
使用的时候需要引入singlePageNav.min.js
```
<ul class="nav navbar-nav navbar-right">
  <li><a href="#home">首页</a></li>
  <li><a href="#bbs">论坛</a></li>
  <li><a href="#html5">前端开发</a></li>
  <li><a href="#cources">最新课程</a></li>
  <li><a href="#app">移动APP</a></li>
  <li><a href="#contact">联系我们</a></li>
  <li><a href="www.baidu.com">百度</a></li>
</ul>
<script>
$(document).ready(function(){
$(".nav").singlePageNav({
			offset:70
		});
})
</script>
```
**注意:** 给父标签设置了singlePageNav就无法跳转到其他页面了，就比如上面的**百度**连接是不能够跳转出去的，我也不知道为什么，大佬们知道的话告诉下小弟哈。
# chart插件的使用
这个插件主要是生成图标的，就如我后台的那个统计表，非常之帅气。
这个使用需要引入Chart.js和script.js两个文件，script.js里面的主要是配置数据的，这个是需要我们自己手动更改的,在需要用到的地方创建出一个画布canvas
```
<div>
  <canvas id="canvas" class="col-md-12"></canvas>
</div>
```
接着就是配置script.js的数据了
```
//lineChartData里面datasets的每一个对象就是一条线和区域
var lineChartData = {
    //X坐标数据
    labels : ["周一","周二","周三","周四","周五","周六","周末"],
    datasets : [
        {
            //统计表的背景颜色
            fillColor : "rgba(0,0,255,0.5)",
            //统计表画笔颜色
            strokeColor : "#f60",
            //点的颜色
            pointColor : "#000;",
            //点边框的颜色
            pointStrokeColor : "red",
            //鼠标触发时点的颜色
            pointHighlightFill : "red",
            //鼠标触发时点边框的颜色
            pointHighlightStroke : "#000",
            //Y坐标数据
            data : [300,555,655,714,899,905,1000]
        },{
            fillColor : "rgba(0,255,0,0.5)",
            strokeColor : "rgba(92, 184, 92, 1)",
            pointColor : "rgba(23, 126, 23, 1)",
            pointStrokeColor : "#fff",
            pointHighlightFill : "#fff",
            pointHighlightStroke : "rgba(151,187,205,1)",
            data : [314,455,755,814,999,905,1000]
        }
        ,{
            fillColor : "rgba(255,0,0,0.5)",
            strokeColor : "blue",
            pointColor : "rgba(23, 126, 23, 1)",
            pointStrokeColor : "#fff",
            pointHighlightFill : "#fff",
            pointHighlightStroke : "rgba(151,187,205,1)",
            data : [114,255,455,414,599,605,500]
        }
    ]

}

window.onload = function(){
    var ctx = document.getElementById("canvas").getContext("2d");
    window.myLine = new Chart(ctx).Line(lineChartData, {
        responsive: true
    });
}
```
# knockout框架的使用
当然我只是最近在学这个框架，所以顺便实战了一下，这个框架只需要在页面上应用knoucout.js这个文件就ok了，这个框架有点类似于,挺不错的，这个技术我在这里主要是在后台管理中的添加标签的地方有用到，并且将添加的标签添加到H5的localstorage里面去，具体实现方式去代码里面去看吧


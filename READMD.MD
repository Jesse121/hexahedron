### 旋转的六面体
这是用CSS3创建的一个旋转六面体，主要用到了CSS3的animation和transform属性,如果对着两个属性不熟悉的，可以先点击这里熟悉一下 [animation](http://www.w3school.com.cn/cssref/pr_animation.asp) [transform](http://www.w3school.com.cn/cssref/pr_transform.asp)   
为了看到更好的效果请尽可能使用高版本的浏览器 如chrome58 Firefox53 IE11等  
实例效果如下：  

<style type="text/css">
    .hexahedron { margin: 100px auto; width: 200px; height: 200px;perspective: 1000px; perspective-origin: 50% 50%;  }
    .top,.bottom,.left,.right,.front,.back { position: absolute; top: 0px; left: 0px; border: 1px solid #000; width: 200px; height: 200px; text-align: center; font: bold 30px/200px "microsoft yahei"; opacity: .6; transition: 1s; }
    .top {animation: opentop 1s linear 0s 1 both;} 
    .bottom { animation: openbottom 1s linear 1s 1 both; }
    .left { animation: openleft 1s linear 2s 1 both; }
    .right { animation: openright 1s linear 3s 1 both; }
    .front { animation: openfront 1s linear 4s 1 both; }
    .back { animation: openback 1s linear 5s 1 both; }
    /*外层包裹使用3d旋转效果*/
    .all { position: relative; width: 100%; height: 100%; transform-style: preserve-3d; animation: animation 6s both linear 6s infinite; }
    .all:hover .top { color: #fff; background: red; }
    .all:hover .bottom { color: #fff; background: orange; }
    .all:hover .left { color: #fff; background: yellow; }
    .all:hover .right { color: #fff; background: green; }
    .all:hover .front { color: #fff; background: cyan; }
    .all:hover .back { color: #fff; background: blue; }
   @keyframes opentop {
     0% {
       transform: none;
     }
     100% {
       transform: translateZ(-100px) rotate3d(1, 0, 0, 90deg);
       transform-origin: 0 0;
     }
   }

   @keyframes openbottom {
     0% {
       transform: none;
     }
     100% {
       transform: translateZ(-100px) rotate3d(1, 0, 0, -90deg);
       transform-origin: 50% 100%;
     }
   }

   @keyframes openleft {
     0% {
       transform: none;
     }
     100% {
       transform: translateZ(-100px) rotate3d(0, 1, 0, -90deg);
       transform-origin: 0 0;
     }
   }

   @keyframes openright {
     0% {
       transform: none;
     }
     100% {
       transform: translateZ(-100px) rotate3d(0, 1, 0, 90deg);
       transform-origin: 100% 50%;
     }
   }

   @keyframes openfront {
     0% {
       transform: none;
     }
     100% {
       transform: translateZ(100px);
     }
   }

   @keyframes openback {
     0% {
       transform: none;
     }
     100% {
       transform: translateZ(-100px);
     }
   }


   @keyframes animation {
     0% {
       transform: rotate3d(0, 0, 0);
     }
     100% {
       transform: rotateX(180deg) rotateY(180deg) rotateZ(180deg);
     }
   }
</style>
<div class="hexahedron">
    <div class="all">
        <div class="top">top</div>
        <div class="bottom">bottom</div>
        <div class="left">left</div>
        <div class="right">right</div>
        <div class="front">front</div>
        <div class="back">back</div>
    </div>
</div>

<a href=""></a>
#### 创建过程
首先创建6个div作为六面体的6个面，初始状态使用绝对定位使6个面堆叠在一起
```html
<style type="text/css">
.top,.bottom,.left,.right,.front,.back { 
    position: absolute; 
    top: 0px; 
    left: 0px; 
    border: 1px solid #000; 
    width: 200px; 
    height: 200px; 
    text-align: center; 
    font: bold 30px/200px "microsoft yahei"; 
    opacity: .6; 
    transition: 1s; /*hover动画用时*/
}
</style>
<div class="all">
    <div class="top">top</div>
    <div class="bottom">bottom</div>
    <div class="left">left</div>
    <div class="right">right</div>
    <div class="front">front</div>
    <div class="back">back</div>
</div>
```
然后分别给6个面设置CSS3动画
```css
/*属性分别是动画名称，动画所花费的时间 动画的速度曲线 
动画开始之前的延迟 动画应该播放的次数 动画时间之外的状态*/
/*这里需要注意设置动画的延迟时间依次增加1s*/
.top { animation: opentop 1s linear 0s 1 both; }
.bottom { animation: openbottom 1s linear 1s 1 both; }
.left { animation: openleft 1s linear 2s 1 both; }
.right { animation: openright 1s linear 3s 1 both; }
.front { animation: openfront 1s linear 4s 1 both; }
.back { animation: openback 1s linear 5s 1 both; }
.all { 
    position: relative; 
    width: 100%; 
    height: 100%; 
    transform-style: preserve-3d; 
    animation: animation 6s both linear 6s infinite; 
}
@keyframes opentop {
 /*设置动画初始状态*/
 0% {
   transform: none;
 }
 /*设置动画最终状态*/
 100% {
   /*Z轴向内移动100px，同时top面沿x轴正向旋转90度*/
   transform: translateZ(-100px) rotate3d(1, 0, 0, 90deg);
    /*设置旋转中心点*/
   transform-origin: 0 0;
 }
}

@keyframes openbottom {
 0% {
   transform: none;
 }
 100% {
   transform: translateZ(-100px) rotate3d(1, 0, 0, -90deg);
   transform-origin: 50% 100%;
 }
}

@keyframes openleft {
 0% {
   transform: none;
 }
 100% {
   transform: translateZ(-100px) rotate3d(0, 1, 0, -90deg);
   transform-origin: 0 0;
 }
}

@keyframes openright {
 0% {
   transform: none;
 }
 100% {
   transform: translateZ(-100px) rotate3d(0, 1, 0, 90deg);
   transform-origin: 100% 50%;
 }
}

@keyframes openfront {
 0% {
   transform: none;
 }
 100% {
   transform: translateZ(100px);
 }
}

@keyframes openback {
 0% {
   transform: none;
 }
 100% {
   transform: translateZ(-100px);
 }
}
/*设置3d旋转动画*/
@keyframes animation {
 0% {
   transform: rotate3d(0, 0, 0);
 }
 100% {
   transform: rotateX(180deg) rotateY(180deg) rotateZ(180deg);
 }
}
```
添加鼠标移上颜色变化效果
```css
.all:hover .top { color: #fff; background: red; }
.all:hover .bottom { color: #fff; background: orange; }
.all:hover .left { color: #fff; background: yellow; }
.all:hover .right { color: #fff; background: green; }
.all:hover .front { color: #fff; background: cyan; }
.all:hover .back { color: #fff; background: blue; }
```
最终为了达到立体透视效果需要在最外层div上添加视距[perspective](http://www.w3school.com.cn/cssref/pr_perspective.asp)元素距离视图的距离，以像素计
```css
.hexahedron { 
    margin: 100px auto;
    width: 200px; 
    height: 200px;
    perspective: 1000px;
    perspective-origin: 50% 50%;  
}
```
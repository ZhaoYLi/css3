# css3
css3魔法
/***********************利用div正方形和伪类的圆形组合*****画心*************************/

.heart{
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%,-50%) rotate(45deg);
	background: red;
	width: 100px;
	height: 100px;
}
.heart:before,
.heart:after{
	content: '';
	position: absolute;
	top: 0;
	left: -50px;
	width: 100px;
	height: 100px;
	background: red;
	border-radius: 50%;
}
.heart:after{	
	top: -50px;
	left: 0;
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/heart.jpg)
/***************利用border结合transparent特性实现*****气泡悬浮框******************/

.bubbly{
	/*居中定位*/
	position: absolute;
	top: 50%;
	left: 50%;
	transform:translate(-50%,-50%);
	/*居中定位结束*/
	background: #23CCFE;
	border-radius: 8px;
	width: 200px;
	padding: 40px 10px;
	text-align: center;
	color: white;
	font-size: 20px;
}

.bubbly:after{
	content:'';
	position: absolute;
	bottom: 0;/*把图像底部边缘设置在其包含元素底边缘的位置*/
	left: 50%;
	border: 34px solid transparent;/*把边框设置为透明色*/
	border-top-color: #23CCFE;/*设置上边框的颜色*/ 
	margin: 0 0 -34px -17px;
	border-left: 0;	/*去掉左边框*/
	border-bottom: 0;/*去掉下边框*/
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/bubbly.jpg)
/***********************利用线性渐变实现*****切角*****************************/

.cut{
	position: absolute;
	top: 50%;
	left: 50%;
	transform:translate(-50%,-50%);
	width: 200px;
	padding: 60px 20px;/*在div只设置宽度，没设置高度的时候，必须设置padding，否则div在视觉上会消失*/
}
.cut{
	background:
	 linear-gradient(135deg,transparent 15px, pink 0)
	 top left,  /*135度方向，从透明线性渐变到粉色，透明占到15px,而粉色一直渐变到底*/
	 linear-gradient(-135deg,transparent 15px, pink 0)
	 top right,
	 /*top right 即移动背景去相应的地方，background:top right 其实是
	  * background-position:top right 的缩写*/
	 linear-gradient(-45deg,transparent 15px, pink 0)
	 bottom right,
	 linear-gradient(45deg,transparent 15px, pink 0)
	 bottom left;
	 background-size: 50% 50%; 
	 /*设置背景长和宽各为元素的一半。也就是如果你的背景是张图片，那么这张图片占
	  * 你元素的1/4，然后会生成4个这样的图片*/
	 background-repeat: no-repeat;
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/cut.jpg)
/***********************利用径向渐变实现*****弧形切角*****************************/

.arc{
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50% 50%);
	width: 200px;
	height: 200px;
}
.arc{
	background:
	radial-gradient(circle at top left,transparent 15px,yellowgreen 0)
	top left,
	/*circle at top left,渐变路径:从左上圆形，(路径还有一个椭圆的参数:ellipse)*/ 
	radial-gradient(circle at top right,transparent 15px,yellowgreen 0)
	top right, 
	radial-gradient(circle at bottom left,transparent 15px,yellowgreen 0)
	bottom left, 
	radial-gradient(circle at bottom right,transparent 15px,yellowgreen 0)
	bottom right;
	background-size:50% 50% ;
	background-repeat: no-repeat;
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/arc.jpg)
/***********************混合模式背景图**********************************/

.colorful-background{
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50% -50%);
	width: 300px;
	height: 200px;
    text-align: center;
    color: #fff;
    font-size: 200%;
    border-radius: .5em;
    background: 
       linear-gradient(limegreen,transparent),
       linear-gradient(90deg,skyblue,transparent),
       linear-gradient(-90deg,coral,transparent);
    background-blend-mode: screen;
    /*定义了背景层的混合模式，screen:滤色模式*/
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/colorful-background.jpg)
/********************利用线性渐变、阴影、旋转实现太阳*********************************/

.sun{
	position: absolute;
	top: 50%;
	left: 50%;
	width: 200px;
	height: 260px;
	transform: translate(-50%,-50%);
	background: #0BF;
	border-radius: 5px;
}
.sun:before{
	content: '';
	position: absolute;
	width: 80px;
	height: 80px;
	left: 50%;
	top: 50%;
	transform: translate(-50%,-50%);
	border-radius: 50%;
	background: rgba(255,238,68,1);
	box-shadow: 0 0 0 15px rgba(255,255,0,0.2),0 0 15px #fff;
	z-index: -10;	
}
.sun:after{
	content: '';
	position: absolute;
	top: 50%;
	left: 50%;
	height: 160px;
	width: 160px;
	transform: translate(-50%, -50%) rotate(30deg);
	z-index:-100;
	/*webkit内核的safari,chrome*/
	background-image: 
	-webkit-linear-gradient(top, rgba(255,255,255,0) 0%,rgba(255,255,255,0.8) 50%,rgba(255,255,255,0) 100%),
	-webkit-linear-gradient(left, rgba(255,255,255,0) 0%,rgba(255,255,255,0.8) 50%,rgba(255,255,255,0) 100%);
	background-size: 20px 100%, 100% 20px;/*双重背景*/
	background-repeat: no-repeat;
	background-position: center center,center center;
	animation:sunRotate 10s linear infinite;
}
@keyframes sunRotate{
	0%{
		transform: translate(-50%, -50%) rotate(30deg);
	  }
	100%{
		transform: translate(-50%, -50%) rotate(390deg);
		}
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/sun.gif)
/***********************利用border、box-shadow 实现*****彩虹*******************/

.rainbow-container{
	position: absolute;
	top: 50%;
	left: 50%;
	width: 200px;
	height: 260px;
	transform: translate(-50% -50%);
	background: #f3d166;
	border-radius: 5px;
}
.rainbow{
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50% -50%);
	height: 1px;
	width: 1px;
}
.rainbow:before{
	content: '';
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%,-50%) rotate(45deg);
	height: 70px;
	width: 70px;
	border-radius: 100px 0 0 0;
	box-shadow: 
	        #F44336 -2px -2px 0 1px,
            #FF9800 -4px -4px 0 3px,
            #FFEB3B -6px -6px 0 5px,
            #8BC34A -8px -8px 0 7px,
            #00BCD4 -10px -10px 0 9px,
            #2196F3 -12px -12px 0 11px,
            #9C27B0 -14px -14px 0 13px;/*参数依次为：水平阴影位置、垂直阴影位置、模糊距离、阴影大小*/
            animation: rainbow 5s ease-in-out infinite;
	
}
.rainbow:after{ 
	content: '';
	position: absolute;
	top: 70px;
	left: 50%;
	height: 15px;
	width: 120px;
	background: rgba(0,0,0,.5);
	border-radius: 50%;
	transform: translate(-50%,-50%);
	animation: cloudy_shadow 5s ease-in-out infinite;/*ease-in-out规定以慢速开始和结束*/	
}
@keyframes rainbow{
	50%{
		transform: translate(-50%,-55%) rotate(30deg);/*rotate()顺时针旋转*/
	}
	100%{
		transform: translate(-50%,-50%) rotate(45deg);
	}
}
@keyframes cloudy_shadow{
	50%{
		transform: translate(-50%,-50%) scale(0.8);
		background: rgba(0,0,0,.2);
	}
	100%{
		transform: translate(-50%,-50%) scale(1); /*translate()根据左(X轴)和顶部(Y轴)位置给定的参数，从当前元素位置移动。scale()放大或缩小*/
		background: rgba(0,0,0,.5);
	}
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/rainbow.gif)
/***********************利用border、transparent、旋转 实现*****五角星*******************/

.five-star{
	position: absolute;
	top: 35%;
	left: 50%;
	transform: translate(-50%,-50%) scale(8);
	width: 0;
	height: 0;
	display: block;
	border-left: 3.04px solid transparent;
	border-right: 3.24px solid transparent;
	border-bottom: 10px solid #B4D5FE;
	-webkit-filter: drop-shadow(1px .5px 1px # ccc);/*filter的阴影滤镜drop-shadow. 参数:(X偏移  Y偏移 模糊大小  色值)*/
	cursor: pointer;
}
.five-star:before{
	content: '';
	position: absolute;
	top: 8.65px;
	left: -9px;
	width: 0;
	height: 0;
	color: #B4D5FE;
	display: block;
	border-left: 12.5px solid transparent;
	border-right: 12.5px solid transparent;
	border-bottom: 9.08px solid #B4D5FE;
	transform-origin: top center;/*设置元素旋转的基点位置*/
	transform: rotate(36deg);
}
.five-star:after{
	content: '';
	position: absolute;
	top: 8.65px;
	left: -15px;
	width: 0;
	height: 0;
	color: #00A65A;
	display: block;
	border-left: 12.5px solid transparent;
    border-right: 12.5px solid transparent;
    border-bottom: 9.08px solid #B4D5FE;
    transform-origin: top center;
    transform: rotate(-36deg);
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/five-star.jpg)
/**************利用切角、渐变、伪类、旋转 实现*****折角*******************/

.corner{
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%,-50%);
	width: 120px;
	height: 120px;
	padding: 40px;
	background: linear-gradient(-150deg,transparent 1.5em,skyblue 0);
	border-radius: 8px;
}
.corner:before{
	content: '';
	position: absolute;
	top: 0;
	right: 0;
	background:
	  linear-gradient(to left bottom,transparent 50%,rgba(0,0,0,.2)0,rgba(0,0,0,.4)) 100% 0 no-repeat;
    width: 1.73em;
    height: 3em;
    transform: translateY(-1.3em) rotate(-30deg);
    transform-origin:bottom right;
    border-bottom-left-radius:inherit;/*设置元素左下角样式*/
    box-shadow: -.2em .2em .3em -.1em rgba(0,0,0,.15);
}
![image](https://github.com/ZhaoYLi/css3/blob/master/img/corner.jpg)










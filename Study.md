
#自从上次写的一下子不见之后我知道了提交上传的重要性谢谢 （保存是个好习惯么么砸）##
##10/28/2015 6:08:35 PM （学习遇到的问题以及解决方法）
####关于js中getComputedStyle()的使用
eg：

    var element=document.getElementById("box");
    var a=window.getComputedStyle(element,null);//是该元素所有的CSS样式声明对象


但是在ie9以下不支持，ie中获取的方法是：

    var element=document.getElementById("box");
    var t= m.currentStyle.opacity;

所以来个通用的

    var element=document.getElementById("box");
	var t= m.currentStyle?m.currentStyle.opacity:window.getComputedStyle(m,null).opacity；
	//这是获取透明度；ie和chorm的方式是不同的
     obj.style.opacity=(t+speed)/100;  //chorm
     obj.style.filter='alpha(opacity.'+(t+speed/100)+')';  //ie;

####关于css的border，padding
浏览器最终出现的div的border，padding，margin等属性，是在浏览器读取了代码的值之后，最后加上的
eg:

		setInterval(function(){
		element.style.width=element.offsetWidth-1+'px';),30)
      
       此时css的设定里element的boder=1px；
       这时这个element不会减小反而增大；增大的速度是1；因为两边border各加1为2

###关于js里获取元素宽度
offsetwidth获取的是整个值，包括了padding，margin，border
如果想获取单纯的width 可以写在元素的行内或者用上面的那个getComputedStyle；

####js小数的取舍
Math.round();四舍五入
Math.floor(25.5);25
Math.ceil(25.5);26


####js对象的某个属性或者如果是个变量
 比如student是个对象里面有name age 属性，在某个页面用var attr存了name或者age，访问时不能
sutudent.attr;这样访问不到要用中括号student[attr]

####动画效果

1.   从CSS3来看
  
 -  三个基本属性(transition,animation,transform)
 -  transition:
 -  transfprm :要结合transition才有动画，它本身只是单纯的状态，支持3D

2. 从JS来看（看函数库里的Action）


####css里的div包含img，底部出现缝隙（vertical-align和line-height。）####

		<div class="box"><img src=""></div>

在css代码中加入
       
      img{
        vertical-align: bottom;//文字并排

		}
或者
		
		  img{
        /*vertical-align: bottom;*/
        display: block;//文字跳行
    }
或者

	#box{
        background-color: #31b0d5;
        /*line-height:30px;*/
        /*display: inline-block;*/
    }


####css垂直居中####
html

	<div id="box3"><img src="6.jpg">xxx</div>

css

    #box3{
        background-color: #31b0d5;
        line-height:600px;
        font-size: 0;
        width: 800px;
	;
    }

    img{
        vertical-align: middle;
        width:400px;
        height:300px;
        /*display: block;*/
    }

####css基本完全居中####
css代码：

       .box{
			  margin: auto;
			  position: absolute;
			  top: 0;
			  left: 0;
			  bottom: 0;
			  right: 0;
		}
html:
  
            <div class=box><p class="text">我喜欢的样子你都有</p></div>

ps
可以在这个box里写文字(box设置position:relation)：

- 文字居中

<img src="img/1.png" style="height:300px;">

css
 
	.box{
			  margin: auto;
			  position: absolute;
			  top: 0;
			  left: 0;
			  bottom: 0;
			  right: 0;
		}
		 .text{
            width: 50%;
            height:50%;
            overflow: hidden;
            margin: auto;
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            right: 0;
        }

- 文字靠右
<img src="img/2.png" style="height:300px;">

      将上面left改为auto

####transition点击出现效果

eg：

css代码
		
		<input type="checkbox" id="button">
		<label class="ani" for="button"></label>
html代码
	
		input{display:none}
		.ani
	    	{
	    width:100px;
	    height:100px;
	    background:red;
	    transition:width 2s;
	    -moz-transition:all 2s; /* Firefox 4 */
	    -webkit-transition:all 2s; /* Safari and Chrome */
	    -o-transition:width 2s; /* Opera */
	    display:block;
	    }
	input:checked + .ani{width:300px;background-color:blue;}
	

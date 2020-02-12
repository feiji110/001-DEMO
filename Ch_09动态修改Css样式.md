### 1.this.style.backgroundColor
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>newWindow</title>
    <style>
        #container{
            height:200px;
            width:200px;
        }
    
    </style>
</head>
<body>
    <div id = "container" style="background: red;"> </div>
</body>
<script>
    //DOM对象.style这里的style也是一个对象，封装了元素的所有样式属性，样式名的写法：单个字母
    // 就是小写。如果是多个单词的样式，backgroundColor第一个单词小写，以后的单词首字母大写。
    var container = document.getElementById("container");
    container.onclick = function(){
        console.log(this.getAttribute("style"));//得到属性值字符串
        console.log(this.style);//很长的一个对象。所有样式包装成一个对象。HTMLDOM
        this.style.backgroundColor = "blue"; //通过style属性新增样式为行内样式，（直接在元素标签上有显示）优先级高，所以可以覆盖业内样式。
        this.style.width = "400px";
        var bg = this.style.backgroundColor;
        console.log(bg);
        console.log(this.style.height);//非行内样式无法获取
        //使用style获取样式，该样式必须是元素的行内样式才能获取。
    } 
</script>
</html>
````
### 2.(parseInt(bg.style.marginLeft)+1)+"px"简单动画
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>newWindow</title>
    <style>
        .bg{
            height:200px;
            width:200px;
            background: red;
        }
    
    </style>
</head>
<body>
    <div class = "bg" style="margin-left: 0;"> </div>
    <button id = "btn1">开始</button>
    <button id = "btn2">停止</button>
</body>
<script>
    // marginLeft,一点一点向左移动：setInterval引出透明度，高度；---由固定数值设置---渐变匀速动画
    var bg = document.getElementsByClassName("bg")[0];//得到类数组遍历或者加索引得到单个
    var btn1 = document.getElementById("btn1");
    var btn2 = document.getElementById("btn2");
    // 定义全局变量
    var intervalId;
    btn1.onclick = function(){
        // alert(bg.style.marginLeft)
        intervalId = setInterval(function(){
            if(parseInt(bg.style.marginLeft)>=20){
                clearInterval(intervalId);
                // return;
             }
            bg.style.marginLeft = (parseInt(bg.style.marginLeft)+1)+"px";//去掉单位
        },30)
        // if(parseInt(bg.style.marginLeft)>=200){
        //     clearInterval(intervalId);
        // }
    }
    btn2.onclick = function(){
        clearInterval(intervalId);//不定义成全局的在其他函数获取不到
    }
</script>
</html>
````
### 3. 
- backg
- fontSize
- fontFamily
- fontWeight
- marginLeft
- paddingLeft
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>newWindow</title>
    <style>
        #container{
            height:200px;
            width:200px;
            background: red;
            margin-left: 10px;
        }
        #container:hover{
            margin-left: 30px;
            background: blue;
        }
    
    </style>
</head>
<body>
    <div id = "container" style="margin-left: 20px;"> </div>
 
</body>
<script>
    // Window.getComputedStyle(DOM对象，伪类);
    // 获取网页元素最终起作用的样式，返回值是一个对象，对象里面是样式的属性，属性值。得到的样式是只读的。   
    var container = document.getElementById("container");
    container.onclick = function(){
        // DOM对象.currentStyle,限定于IE浏览器获得样式
        if(container.currentStyle){
            console.log(container.currentStyle["marginLeft"]);
        }
        var objStyle = getComputedStyle(this,"hover");//里面写DOM对象,第二个参数可不写或写null
        console.log(objStyle.backgroundColor);
        console.log(objStyle["marginLeft"]);
    }

</script>
</html>
````
### 4.aninmate
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>newWindow</title>
    <style>
        #container{
            height:200px;
            width:200px;
            background: red;
        }
    </style>
</head>
<body>
    <div id = "container" > </div>
 
</body>
<script>
// 得到对象的样式
function getStyle(obj){
    if(obj.currentSyle){
        return obj.currentStyle;
    }else{
         return getComputedStyle(obj);
    }
}
function animate(obj,jsonObj,callback){
    var intervalId = setInterval(function(){
        for(var i in jsonObj){
            // console.log(jsonObj);
            getStyle(obj)["width"];
            var endStyle = parseInt(jsonObj[i]); 
            var startStyle = parseInt(getStyle(obj)[i]);
            // console.log( endStyle + startStyle);
            var speed = (endStyle-startStyle)/8;
            speed = speed>0?Math.ceil(speed):Math.floor(speed);//使之成为整数
            if(i == "opacity"){


            }else{
                obj.style[i] = (startStyle + speed) + "px";
                if(parseInt(getStyle(obj)[i])==parseInt(jsonObj[i])){
                    delete jsonObj[i];
                }
                if(JSON.stringify(jsonObj) == "{}"){
                    clearInterval(intervalId);
                    callback();
                }
                console.log(jsonObj);
            }
        }
    }
    ,30)
}
var container = document.getElementById("container");
function callback1(){
    console.log("回调函数1");
}
animate(container,{"width":1000,"height":400,"marginLeft":200},callback1);

</script>
</html>
````
### 5.
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>更新</title>
    <style>
        .bg{
            height:200px;
            width:200px;
            background: red;
            margin-left:50px;
        }
    
    </style>
</head>
<body>
    <div class = "bg" > </div>
    <button id = "btn1">开始</button>
    <button id = "btn2">停止</button>
</body>
<script>
    // marginLeft,一点一点向左移动：setInterval引出透明度，高度；---由固定数值设置---渐变匀速动画
    var bg = document.getElementsByClassName("bg")[0];//得到类数组遍历或者加索引得到单个
    var btn1 = document.getElementById("btn1");
    var btn2 = document.getElementById("btn2");
    bg.style.marginLeft = getComputedStyle(bg)["marginLeft"];
    // alert(bg.style.marginLeft);
    // 定义全局变量
    var intervalId;
    btn1.onclick = function(){
        // alert(bg.style.marginLeft)
        intervalId = setInterval(function(){
            if(parseInt(bg.style.marginLeft)>=200){
                clearInterval(intervalId);
                // return;
             }
            bg.style.marginLeft = (parseInt(bg.style.marginLeft)+1)+"px";//去掉单位
        },30)
        // if(parseInt(bg.style.marginLeft)>=200){
        //     clearInterval(intervalId);
        // }
    }
    btn2.onclick = function(){
        clearInterval(intervalId);//不定义成全局的在其他函数获取不到
    }
</script>
</html>
````
### 调用animate
````js
<!DOCTYPE html>
<html>
<head>
    <title>demo</title>
    <meta charset = "UTF-8">
    <style>
        #banner{
        width:100px;
        height:100px;
        background:red;
        position:absolute;
        left:0;
        }
    </style>
</head>
<body>
    <div id = "banner"></div>
</body>
<script src="../JS/_animate.js"></script>
<script>
    var banner = document.getElementById("banner");
    animate((banner),{left:300},function(){
        alert("执行结束");
    })
</script>
</html>
````

### 兼容提取样式
````js
function getStyle(obj,attr){
    if(obj.currentStyle){
        return obj.currentStyle[attr];
    }else{
        return getComputedStyle(obj,null)[attr];
    } 
}
````
### 变速运动

````js
 var timer = setInterval(function(){
     var now = parseInt(getStyle(box,'left'));
     var speed = (333-now)/6;
     speed = speed>0?Math.ceil(speed):Math.floor(speed);
     if(now == 333){
         clearInterval(timer)
     }else{
         box.style.left = now + speed + "px";
     }
 },30)
 ````
### 事件对象
````js
<script>
    window.onload = function(e){
        console.log(e);
        //浏览器给回调函数的对象信息
        
    }
</script>
````
### event
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>事件对象</title>
    <style>
        *{
            padding:0;
            margin:0;
        }
        #bg{
            height:300px;
            width:300px;
            background: red;
        }
    </style>
</head>
<body >
    <div id = "bg"></div>
    <input type="text" onkeypress="showCode(event)"/>
    <a href="http://www.baidu.com" id="link">link</a>
</body>
<script>
    //事件对象·，在事件被触发时，有浏览器自动传递事件的回调函数。
    //e.clientX e.clientY 相对于浏览器窗口的左上角的位置坐标
    var bg = document.getElementById("bg");
    var link = document.getElementById("link");

    bg.onclick = function(e){
        // console.log(e.clientX,e.clientY);
        // console.log(e.screenX,e.screenY);
        // // console.log(e.pageX,e.pageY);
        // console.log(e.button);
        // // console.log(e.keyCode);//undefined
        // //console.log(e.which);
    }
    function showCode(e){
        //console.log(e.which);//浏览器兼容 
        console.log(e.keyCode);        
    }
    link.onclick = function(e){
        e.preventDefault();
    }
</script>
</html>
````
### 
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>newWindow</title>
    
</head>
<body>
    <div id = "container">
        <button id="btn">子元素</button>
    </div>
 
</body>
<script>
    var container = document.getElementById("container");
    var btn = document.getElementById("btn");
    var bodyObj = document.body;
    btn.onclick = function(e){
        // e.stopPropagation();//阻止向外冒泡
        console.log("按钮被点击了");
    }
    container.onclick = function(e){
        e.stopPropagation();
        console.log(e.target);//表示事件触发的根源元素
        console.log(e.currentTarget);//当前监听事件的元素DOM对象
        console.log(e.timeStamp);
        // console.log("div");
    }
    bodyObj.onclick = function(){
        console.log("body");
    }

</script>
</html>
````
###
````html
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>无标题文档</title>
<style>
	body,ul,li,dl,dt,dd,p,ol,h1,h2,h3,h4,h5,h6,form,img,table,fieldset,legend{margin:0; padding:0;}

	#box{width:750px;height:400px;position:relative; margin:100px auto;border: 1px solid black;}
	#img1{width:300px;height:300px;position:absolute;left:0;top:0;}
	#slider{width:150px;height:150px;position:absolute;left:0;top:0;background:#CCC;opacity:0.4;cursor: move;display:none; filter:alpha(opacity=40);}
	#img2{position:absolute;right:0;top:0;display:none; width:400px;height:400px;overflow:hidden;}
	#Bimg{position:absolute;left:0;top:0;}
</style>
</head>

<body>
 <div id="box">
    <div id="img1">
         <img src="images/small.jpg" width="300" height="300" id="Simg"/>
         <div id="slider"></div>
  	</div>
       
    <div id="img2">
        <img src="images/big.jpg"  id="Bimg"/>
    </div>
    
  </div>
<script>
    var slider = document.getElementById("slider");
    var img1 = document.getElementById("img1");
    var img2 = document.getElementById("img2");
    var Simg = document.getElementById("Simg");
    var Bimg = document.getElementById("Bimg");
    var box = document.getElementById("box");
    
    img1.onmouseover = function(){
        slider.style.display = "block";
    }
    img1.onmousemove = function(e){
      var mouseX = e.clientX;
      var mouseY = e.clientY;
      //不显示单位，默认以px为单位。
      var boxLeft = box.offsetLeft;
      var boxTop = box.offsetTop;
      console.log(mouseX,mouseY,boxLeft,boxTop);
      var sliderWidth = slider.offsetWidth;//实时获取
      var sliderHeight = slider.offsetHeight;
      var sliderLeft = mouseX - boxLeft - sliderWidth/2;
      var sliderTop = mouseY - boxTop -sliderHeight/2;
      if(sliderLeft <= 0){
          sliderLeft = 0;
      }
      else if(sliderLeft >= (img1.offsetWidth - slider.offsetWidth)){
        sliderLeft = (img1.offsetWidth - slider.offsetWidth);
      }
      if(sliderTop <= 0 ){
        sliderTop = 0;
      }
      else if(sliderTop >= (img1.offsetHeight - slider.offsetHeight) ){
          sliderTop = img1.offsetHeight - slider.offsetHeight;
      }
      slider.style.left = sliderLeft + "px";
      slider.style.top = sliderTop + "px";
      
    }
</script>
</body>
</html>

````

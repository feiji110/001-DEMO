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

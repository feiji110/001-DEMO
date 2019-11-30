### 内置对象Date
````js
/*
自定义：通过var
内置对象：Node在后端运行
宿主对象：因为环境，windos对象于document对象只能在浏览器中用
*/
var date1 = new Date();
console.log(date1.toLocaleString());//获取完整年份

var year = date1.getFullYear();
var month = date1.getMonth() + 1;//getMonth()得到的结果是0-11
var currentDate = date1.getDate();//getDate()仅仅得到日
var days = ["周日",'周一',"周二","周三","周四","周五","周六"]
var currentDay = date1.getDay();//getDay()仅仅获得星期几的索引，取值范围0-6，公认周日为第一天
console.log(year,month,currentDate,days[currentDay]);//星期1是第二天//为啥有双引号？

var hour = date1.getHours();
var minute = date1.getMinutes();
var second = date1.getSeconds();
console.log(hour,minute,second);
````
### 练习
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <p id = "timer"></p>
    <button id = "btn">获取当前时间</button>
</body>
<script type="text/javascript" >
    //当点击btn按钮时，设置p标记标签内部内容为当前时间，格式2019-10-14 10:13:20
    var btn = document.getElementById("btn");
    var timer = document.getElementById("timer");
    btn.onclick = function(){
    var date1 = new Date();
    var year = date1.getFullYear();
    var month = date1.getMonth()+1;
    var date = date1.getDate();
    var hour = date1.getHours();
    var minute = date1.getMinutes();
    var second = date1.getSeconds();

    var dateStr = year + "-" + month + "-" + date +" " + hour + ":" + minute + ":" +second;
    timer.innerHTML = dateStr;

    }
</script>
</html>
````
### BOM
1. ECMAscript 语言标准 变量的定义及类型
2. Browser Object Model :将整个浏览器进行抽象，帮助我们对浏览器进行控制
+ 顶层对象：Window 
+ History对象:让页面前进与后退
+ Location:
+ document对象：网页DOM对象比较复杂，最核心
````js
//因为Window对象时最顶层的全局对象，定义在Window对象方法的使用，一般省略Window。
window.alert("提示框1");
var result = window.confirm("是否确认删除？");
//confirm会有一个返回值
if(result){
    console.log("用户点击了确认");
}
else{
    console.log("用户点击了取消");
}
//可以自定义一个div来自设置一个美化的confirm框

var pr = prompt("请输入姓名：","默认值");
alert(pr);
````
### demo
````js
//在输入框中可以输入算数运算式，点击确认时将结果用alert弹出
var pr = prompt("请输入一个算式：");
alert(eval(pr));
//输入  用户名;密码,验证输入是否为admin 123
var pr = prompt("请输入用户名密码");
var arr = pr.split(";");
if(arr[0] == "admin" && arr[1] == "123"){
    alert("Success");
}
else{
    alert("fail");
}
````
### 延迟执行
````html
//var intervarId = setTimeout(fn , timeout)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Demo</title>
</head>
<body>
    <button id ='stop' >   停止延迟执行</button>
</body>
<script>
    var intervalId = setTimeout(function(){
          alert("延迟了3s执行的");
    },3000);//默认ms
    var stop = document.getElementById("stop");
    stop.onclick = function(){
         clearTimeout(intervalId);//清除延迟执行
    }
</script>
</html>
````
### 清除定时执行
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Demo</title>
</head>
<body>
    <button id ='stop' > 清除定时执行</button>
</body>
<script>
    var intervalId = setInterval(callback,1000);//默认ms
    function callback(){
        console.log((new Date()).toLocaleString());
    }
    var stop = document.getElementById("stop");
    stop.onclick = function(){
        clearInterval(intervalId);
    }
</script>
</html>
````
### exercise_2
````html
    //点击开始按钮，每个1秒加1，停止按钮，停止加1
   
    // start.onclick = function(){
    //     intervalId = setInterval(function(){
    //         clearInterval(intervalId);
    //         countNum = countNum + 1;
    //         count,innerHTML = countNum;
    //     },1000)
    // }
    //  stop.onclick = function(){
    //     clearInterval(intervalId);
    // }
 <p id = "count">0</p>
    <button id = "start">开始计数</button>
    <button id = "stop">停止计数</button>
````
### 动态得到时间
````html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Demo</title>
</head>
<body>
   <p id="timer"></p>
</body>
<script> 
    var timer = document.getElementById("timer");
    var intervalId = setInterval(function(){
        var date1 = new Date();
        var hour =date1.getHours();
        var minute = date1.getMinutes();
        var second =date1.getSeconds();
        timer.innerHTML = hour + ":" + minute + ":" +second;
    },1000);
</script>
</html>
````

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Demo</title>
</head>
<body>
    <p id = "count">0</p>
    <button id = "start">开始计数</button>
    <button id = "stop">停止计数</button>
</body>
<script> 
    var count = document.getElementById("count");
    var start = document.getElementById("start");
    var intervarId = 0;
    start.onclick = function(){
        intervalId = 0;
        intervalId = setInterval(callback,1000);//默认ms
    }
    function callback(){
        count.innerHTML++;
    }
    var stop = document.getElementById("stop");
    stop.onclick = function(){
        clearInterval(intervalId);
    }
</script>
</html>
````
````javascript
var intervalId = setTimeout(function(){
    alert("延迟了3s执行的");
},3000);//默认ms
var stop = document.getElementById("stop");
stop.onclick = function(){
    clearTimeout(intervalId);
}
````







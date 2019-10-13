
### JS语句块
````js
if(true){
      document.write("第一条语句执行");
      document.write("<br/>");
      document.write("第二条语句执行");
   }
````
### JS输出语句
````js
document.write("在页面输出内容");
console.log("控制台调试信息");
alert("弹出框提示信息");
````
### 原始数据类型
````js

var a = 200;   //整型 Number
var b = 92.5;   //浮点型 Number
var c = "I'm String";   //字符串型 String
var d = true;   //布尔类型
var e;    //undefined型
var f = null;   //object型
alert(typeof c);
````
### isNaN()函数
````js
 //判断NaN的类型
    console.log(typeof NaN);

 //与自身不相等
    console.log(NaN == NaN); //false

 //123是字符串  转换成数字依然为 123  是数字  所以为false
    var str = "123";
    console.log(isNaN(str));

 //123abc是字符串  不能成功转换为数字  所以为true
    var stt = "123abc"
    console.log(isNaN(stt));
````
### 拼接运算符号
````js
//使用"+"拼接字符串
//从左往右计算，当"+"运算符左右为字符串类型时，为拼接符号
    var x = 3;
    var y = "3";
    var z = 5;
    z += y;
    var a = y + z;
    document.write(x+y+'<br/>');
    document.write(z+'<br/>');
    document.write(a+'<br/>');
    document.write(x+y+z+'<br/>');

/*//练习思考
var num=3+3+"5";
console.log(num);
console.log(typeof num);*/

````
### 比较运算符
````js
var x = 3;
var y = 3;
var z = "3";
alert(x == y);
alert(x === y);
alert(x === z);
````
### 条件运算符
````js
var a = 39;
var b = 30;
document.write(a>=b ? "a大于等于b" : "a小于b");//a大于等于b
var age = 12;
var msg = age>18 ? "成年人" : "未成年";
console.log(msg);//未成年
````
### 转换为字符串类型
````js
   //隐式转换为字符串类型最简单的方法就是  ""+  拼接
   console.log(""+true);//true
   console.log(typeof (""+true) );//String
   console.log(""+false);//false
   console.log(typeof (""+false) );//String
   console.log(""+ 123);//123
   console.log(typeof (""+ 123) );//String
   console.log(""+NaN);//NaN
   console.log(typeof (""+ NaN) );//String
   console.log(""+undefined);//undefined
   console.log(typeof (""+undefined) );//String
   console.log(""+null);//null
   console.log(typeof (""+null) );//String
   //强制转换
   var str = 123;//true false  null undefined
   console.log(String(str));
````
###  2-8转换为布尔值
````js
//隐式转换
//加一个！代表获取变量的相反布尔值，
//加两个 !! 代表获取变量本身的布尔值

console.log(!!0); //false
console.log(!!-0); //false
console.log(!!0.0); //false
console.log(!!NaN); //false
console.log(!!123); //true
console.log(!!undefined); //false
console.log(!!null); //false
console.log(!!""); //false
console.log(!!" "); //true
console.log(!!"hello world");
//强制转换
console.log(Boolean("123"));
console.log(Boolean(""));
console.log(Boolean(" "));
console.log(Boolean(123));
console.log(Boolean(null));
console.log(Boolean(undefined));
````
### 2-9转换为数值类型
````js
//隐式转换为数值类型最简单的方法就是  *1
console.log(false * 1); //0
console.log(true * 1); //1
console.log(undefined * 1); //NaN
console.log(null * 1); //0
console.log("" * 1); //0
console.log(" " * 1); //0
console.log("123" * 1); //123
console.log("123abc" * 1); //NaN
console.log("1a2b3c" * 1); //NaN
//强制转换
var str = "123.5abc";//true false  "1a2b3c" null undefined
console.log(parseInt(str));
console.log(parseFloat(str));
console.log(Number(str));
````
### 2-10转换为字符串类型
//隐式转换为字符串类型最简单的方法就是  ""+  拼接
console.log(""+true);//true
console.log(typeof (""+true) );//String
console.log(""+false);//false
console.log(typeof (""+false) );//String
console.log(""+ 123);//123
console.log(typeof (""+ 123) );//String
console.log(""+NaN);//NaN
console.log(typeof (""+ NaN) );//String
console.log(""+undefined);//undefined
console.log(typeof (""+undefined) );//String
console.log(""+null);//null
console.log(typeof (""+null) );//String
//强制转换
var str = 123;//true false  null undefined
console.log(String(str));
### 数据类型转换练习
````js
//转换为 Number 类型
var a = '123.456img';
var a1 = parseInt(a);
var a2 = parseFloat(a);
var a3 = Number(a);  
document.write("a1="+ a1 + '<br/>'+"a2="+ a2+ '<br/>'+"a3="+ a3+ '<br/>');
document.write(typeof a2 +"<br/><br/>");

//转换成String类型
var b = 3.1415926;
var b1 = b + "";
var b2 = String(b);
document.write(typeof b1 +"<br/>");
document.write(typeof b2 +"<br/><br/>");

//转换成Boolean类型
var c = "img" + 3 + ".jpg";
var c1 = !!c;
document.write("c1 = "+c1+ '<br/>');
document.write(typeof c1);
````
### 2-12数据类型转换规则
````js
// + 是拼接 还是 加号 ？？？
var a = 3;
var b = ".jpg";
var c = 5;
var d = "189";
var  add1 = a + b;
var  add2 = a + c;
var  add3 = a + b + c;
var  add4 = a + c + b;
var  add5 = a + d;
console.log(add1);
console.log(add2);
console.log(add3);
console.log(add4);
console.log(add5);

//其他算数运算符  -  * /  %
var t = "20";
var r = 10;
var p = true;
var q = false;
var count1 = t - r;
var count2 = t - p;
var count3 = t - q;
var count4 = r- p;
var count5 = r - q;
console.log(count1);
console.log(count2);
console.log(count3);
console.log(count4);
console.log(count5);


//布尔类型计算
var x = true;
var y = false;
var sum1 = 99 + x;
var sum2 = 99 + y;
var sum3 = "99" + x;
var sum4 = "99" + y;
console.log(sum1);
console.log(sum2);
console.log(sum3);
console.log(sum4);
````
### 2-13条件语句
````js
var box = 100;
if (box >= 100) {
   alert("甲");
} else if (box >= 90) {
   alert("乙");
} else if (box >= 80) {
   alert("丙");
} else if (box >= 70) {
   alert("丁");
} else if (box >= 60) {
   alert("及格");
} else {
   alert("不及格");
}
````
### 2-14分支语句
````js
var score = "优";
switch (score) {
   case "优":
      document.write("该同学成绩优异");
      break;
   case "良":
      document.write("该同学成绩良好");
      break;
   case "及格":
      document.write("该同学成绩及格");
      break;
   case "不及格":
      document.write("该同学成绩不及格");
      break;
   default:
      document.write("该同学成绩未知");
````
### 2-15f循环
````js
//for循环

for (var i = 1; i < 10; i++) {
   console.log(i);
}

//for循环嵌套
for (var x = 1; x < 10; x++) {
   for (var y = 1; y < 10; y++) {
      console.log(x + "-" + y);
   }
}
//while循环
var i = 1; //i=3;
while (i < 3) {
   document.write(i + "<br/>");
   i++;
}
//do while循环
var i = 1; //i=3;
do {
   document.write(i + "<br/>");
   i++;
} while (i < 3)
````
### 2-16break 和 continue
````js
//break 语句用于跳出循环。continue 用于跳过循环中的一个迭代。
//判断是否是5的倍数
for (var i = 2; i < 12; i++) {
    if (i % 5 == 0) {
        continue; //结束本次循环
        //break;//结束循环体
    }
    document.write(i + "<br/>");
}
//  只输出 0 ，1 ，2 ，到3就跳出循环了
for (i = 0; i < 5; i++) {
    if (i == 3) break;
    console.log(i);


    //  不输出3，因为continue跳过了，直接进入下一个迭代
    for (i = 0; i <= 5; i++) {
        if (i == 3) continue;
        console.log(i);
    }
````
### 2-17练习
````js
//使用for循环，向文档中动态写入一个4行4列的表格，表格单元格内容为&nbsp;
    document.write('<table border="1" cellspacing="0">');
    for (var i = 0; i < 4; i++) {
        document.write("<tr>");
        for (var j = 0; j < 4; j++) {
            document.write("<td>&nbsp;</td>");
        }
        //document.write("</tr>");//可写可不写
    }
    // document.write("</table>");//可写可不写
    </script>

    <script>
 //使用while循环，向文档中动态写入一个4行4列的表格，表格单元格内容为&nbsp;
    var x = 0;
    document.write('<table border="1" cellspacing="0">');
    while (x < 4) {
        document.write("<tr>");
        var y = 0; //注意
        while (y < 4) {
            document.write("<td>&nbsp;</td>");
            y++;
        }
        x++;
    }
````

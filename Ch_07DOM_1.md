> 浏览器各个部分进行抽象
## Ch_07DOM
> HTML与XML DOM是对核心DOM的补充。
### BrotherNodes&getElementById直接获取元素对象
````html
<!DOCTYPE html>
<html lang="en">
<!-- childNodes类数组集合：head,body,script -->
<!-- firstChild -->
<head>
    <meta charset="UTF-8">
    <title>demo</title>
    <style>
        #container{
            height: 200px;
            width: 200px;
            background: red;
        }
    </style>
</head>
<body>
    <!-- 兄弟节点必须有共同父节点 -->
    <div id="container">
        <p>子节点</p>
    </div>
    <div id="container1">
        <p>子节点</p>
    </div>
</body>
<!-- <script src="../JS/demo.js"></script> -->
<!-- lastChild -->
<script > 
/*在对象的方法内部，this指向当前对象*/
var contianer = document.getElementById("container");
console.log(container);

contianer.onclick = function(){
    console.log(contianer.id);
    console.log(this.id);//DOM对象的事件回调函数内部，this指向当前的DOM对象。
}
</script>
</html>
````
### getElementsByClassName&&getElementsByTagName
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>访问元素节点</title>
    <style>
        div{
            height:200px;
            width:200px;
            background: green;
            float:left;
            margin-left: 10px;
        }
       
    </style>
</head>
<body>
    <div id="div1" class="bg">
        div1
    </div>
    <div class="bg">
        div2
    </div>
    <div >
        div3
    </div>
</body>
<script>
    var divList = document.getElementsByTagName("div");
    console.log(divList);
    console.log(divList[0]);
    var div1 = document.getElementById("div1");
    console.log(div1);
    var bgList = document.getElementsByClassName("bg");
    console.log(bgList);
    // [Note] 驼峰命名+elements(TagName&&Class)
</script>
</html>
````
### 得到节点集合，可以当作数组进行处理&&documentElement&&head&&body
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>特殊节点对象的获取</title>
</head>
<body>
   <p>段落1</p>
   <p>段落2</p>
   <p>段落3</p>
</body>
<script>
    // 如果为集合，需要添加索引。所有DOM操作皆针对对象进行。
    var  arr = ["hello", "javascript","!"];
    var pList = document.getElementsByTagName("p");
   for(var i = 0; i < pList.length;i++){
       pList[i].innerHTML = arr[i];
   }
   var htmlDOM = document.documentElement;
   var headDOM = document.head;
   var bodyDOM = document.body; 
</script>
</html>
````
### children&&childNodes
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>间接获取DOM对象之children&childNodes</title>
</head>
<body>
   <ul id="newList">
       <li>子节点</li>
   </ul>
</body>
<script>
    // DOM对象.childNodes 获取子节点对象集合
    // 表示子节点集合，包括空格，注释，实际网页元素
   var newList  = document.getElementById("newList");
   console.log(newList.childNodes);
    // DOM对象.children 获取元素子节点对象集合
    // 只包含具体网页子节点集合，不含空格注释。
    console.log(newList.children);
    for(var i = 0; i <newList.children.length;i++){
        newList.children[i].innerHTML = "元素子节点";    
    }
</script>
</html>
````
### previousSibling&&previousElementSibling&&parentNode
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>previousSibling</title>
</head>
<body>
    <table width = "300px" height="300px" border = "1" align = "center">
        <tr>
            <td></td>
            <td id="tdflag"></td>
            <td>

            </td>
        </tr>
        <tr id="trflag">
            <td></td>
            <td></td>
            <td>
                
            </td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td>
                
            </td>
        </tr>
    </table>
</body>
<script>
    var tdDOM = document.getElementById("tdflag");
    var trDOM = document.getElementById("trflag");
    console.log(tdDOM.previousSibling);//previousSibling包含空格注释
    console.log(tdDOM.previousElementSibling);
    tdDOM.previousElementSibling.innerHTML = "前一个";
    tdDOM.nextElementSibling.innerHTML = "后一个";
    // 获取元素父节点就用parentNode
    tdDOM.parentNode.style.color = "red";//不存在空格注释，另一个含elemrnt存在兼容性问题，所以一般就用这个
</script>
</html>
````
### Exercise1
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Exercise1</title>
</head>
<body>
    <div id = "container">
        <div id = "first" class="bg"></div>
        <div id = "second"></div>
        <div></div>
        <div></div>
        <div id="last"></div>
    </div>
</body>
<script>
//通过last最后一个元素DOM对象得到container中的第一个元素的DOM对象，设置元素内容为第一个子元素
// 尝试用多种方式得到第一个div的DOM对象
var last = document.getElementById("last");
last.parentNode.firstElementChild.innerHTML =  "Morning,Dad!";
var first1 = document.getElementsByTagName("div")[1];
var first2 = document.getElementsByClassName("bg")[0];
var first3 = document.getElementById("first");

var container = document.getElementById("container");
var first4 = container.children[0];
var first5 = container.firstElementChild;

var second = document.getElementById("second");  
var first6 = second.previousElementSibling;
</script>
</html>
````
### innerHTML
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <p id = "p1" >
        段落内容
    </p>
    
</body>
<script>
    var p1 = document.getElementById("p1");
    p1.onclick = function(){
        // p1.innerHTML = "<h1>段落内容</h1>";
        p1.innerHTML = "<img src='https://avatars3.githubusercontent.com/u/43982513?s=400&u=6942404b4850aed167129ffb11b198cf38d5d41b&v=4'/>";
        }
</script>
</html>
````
### getElementsByTagName&&getElementsByClassName&&getElementById
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <ul id = "list">
        <li class='bg'>香蕉</li>
        <li class ='bg'>苹果</li>
        <li class='bg'>橘子</li>
    </ul>
</body>
<script >
//根据id属性得到特定网页元素对应的DOM对象
var list = document.getElementById("list");
//根据网页元素的标记名得到DOM对象的集合（数组）
var arr = list.getElementsByTagName("li");
for(var i = 0; i < arr.length;i++){
    arr[i].innerHTML += i; 
}
var arr1 = list.getElementsByClassName("bg");
for (var j = 0;j<arr1.length;j++){
    arr1[j].style.color = 'red';
}

//childElement.parentNode
//firstElementChild children
//lastElementChild childNodes
</script>
</html>
````
### innerText&&innerHTML
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <ul id = "list">
        <li class='bg'>香蕉</li>
        <li class ='bg'>苹果</li>
        <li class='bg'>橘子</li>
    </ul>
</body>
<script >
var list = document.getElementById("list");
// 设置或获取前面DOM内部对象的HTML内容
// list.innerHTML = '<h1>葡萄</h1>';
//innerText设置的是DOM对象对应的网页元素标记内部的纯文本内容，不解析
// list.innerText = "<h1>葡萄</h1>";
console.log(list.innerText);
// textContent 只有IE可以用，其他有兼容性
</script>
</html>
````
### getAttribute&&setAttribute&&removeAttribute
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>19_11_04</title>
    <style>
    img{
        height:100px;
    }
    .imgborder{
        border:10px solid red;
    }
    #imgmargin{
        margin-left: 200px;
        margin-top: 100px;
    }
    </style>
</head>
<body>
    <img src="logo.png" alt="logo">
    <button id = 'btn1'>添加边框</button>
    <button id = 'btn2'>去除边框</button>
    <button id = 'btn3' >添加外边距</button>
    <button id = 'btn4'>去除外边距</button>
</body>
<script >
var imgList = document.getElementsByTagName("img");
imgList[0].onclick = function(){
    console.log(this.getAttribute("src"));
    this.setAttribute("src","download.png");
    console.log(this.src);
}
var btn1 = document.getElementById("btn1");
btn1.onclick = function(){
    this.previousElementSibling.setAttribute("class","imgborder");
}
var btn2 = document.getElementById("btn2");
btn2.onclick = function(){
    var isExist = this.parentNode.firstElementChild.hasAttribute("class");
    // console.log(isExist);
    if(isExist){
        this.parentNode.firstElementChild.removeAttribute("class");
    }else{
        return;
    } 
}
var btn3 = document.getElementById("btn3");
btn3.onclick = function(){
    this.parentNode.firstElementChild.setAttribute("id","imgmargin");
}
var btn4 = document.getElementById("btn4");
btn4.onclick = function(){
    var isExist = this.parentNode.firstElementChild.hasAttribute("id");
    // console.log(isExist);
    if(isExist){
        this.parentNode.firstElementChild.removeAttribute("id");
    }else{
        return;
    } 
}
</script>
</html>
````
### 
````html


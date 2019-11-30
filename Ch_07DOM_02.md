### getAttribute()&&setAttribute()
````js
var  imgList  = document.getElementsByTagName("img");
var bigpic = document.getElementById("bigpic");
for(var i = 0; i < imgList.length-1;i++){
    imgList[i].onclick = function(){
         bigpic.setAttribute("src",this.getAttribute("src"));
     } 
}
````
````js
var smallPic = document.getElementById("smallpic");
var imgList = smallPic.getElementsByTagName("img");
var bigPic = document.getElementById("bigpic");
// imgList.forEach(function(index,val,arr){
//   console.log(index,val,arr);
// })//仅仅时一个类数组
for(var i = 0; i < imgList.length;i++){
    imgList[i].onclick = function(){
        for(var j = 0; j <imgList.length;j++){
          // imgList[j].setAttribute("class","");
          imgList[j].removeAttribute("class");
        }
        this.setAttribute("class","pb");
        var imgSrc = this.getAttribute("src")
        bigpic.setAttribute("src",imgSrc);
     } 
}
````
### 计算器
````js
	/*
		获取DOM元素绑定点击事件
	*/ 
	/*  1. 获取要操作的网页元素的DOM对象
		2. 给网页元素可以绑定对象
		3. 触发事件时执行事件的回调函数，完成具体的逻辑业务或DOM操作 */
	var result = document.getElementById("result");
	var btnList = document.getElementsByTagName("button");
	for(var i = 0 ;i <btnList.length;i++){
		// 在DOM对象事件的回调函数中，this指向当前触发事件的DOM对象
		btnList[i].onclick = function(){
			var btnType = this.innerHTML;
			switch(btnType){
				case '=':
					calculate();
					break;
				case 'C':
					clearResult();
					break;
				default:
					showStr(btnType);
					break; 
			}
		}
	}
	var str = ""; //定义一个全局变量
	function showStr(val){
		str = result.innerHTML;//包含HTML标记，innerTEXT不含HTML的标记  //重置？？
		if(str == 0){
			str = val;
		}
		else{
			str += val;
		}
		result.innerHTML = str;
	}
	function clearResult(){
		result.innerHTML = "0";//不是0
	}
	function calculate(){
		result.innerHTML = eval(result.innerHTML);
	}
````
### nodeType&nodeValue&nodeName
````js
    //元素节点，属性节点，文本节点都可看作一个对象
    var list = document.getElementById("list");//元素节点的DOM对象
    var linkHref = list.getAttributeNode("href");
    console.log(typeof linkHref);//object
    var textNode = list.firstChild;
    console.log(textNode);
    // nodeType是一个只读属性，只能获取，不能赋值
    console.log(list.nodeType,linkHref.nodeType,textNode.nodeType);
    console.log(list.nodeName,linkHref.nodeName,textNode.nodeName);
    console.log(list.nodeValue,linkHref.nodeValue,textNode.nodeValue);
````
### demo
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>newWindow</title>
</head>
<body>
    <div  id = "container"">
        <p>段落1</p>
        <h3>标题1</h3>
        <div>div1</div>
        <p>段落2</p>
        <h3>标题2</h3>
        <div>div2</div>
    </div>
</body>
<script>
//通过container.children获取container内部段落和div标记内部的内容
// ，存储到数组arr中，在控制台进行输出
var container = document.getElementById("container");
var childList = container.children;
var arr = [];
for(var i = 0; i<childList.length;i++){
    var elName = childList[i].nodeName;
    console.log(childList[i].nodeValue);
    if(elName == "p" || elName == "DIV"){
        arr.push(childList[i].innerHTML);
    }
}
console.log(arr);
</script>
</html>
````
### 雪梨教育作业
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>191111</title>
</head>
<body>
    <button id = 'btn1'>猜数字</button>
    <button id = 'btn2'>输出猜出过的数字</button>  
</body>
<script>
 var btn1 = document.getElementById("btn1");
 var btn2 = document.getElementById("btn2");
 var i = 0;
 btn1.onclick = function(){
        var arr=[];
        var value = parseInt(Math.random()*100);
        // alert(value);
        for(var i = 0; i < 10;i++ ){
            val = prompt("请输入你猜的数字：");
            if(val == value){
                arr[i] = val;
                alert("恭喜你成功猜中数字");
                break;
            }
            else if(val > value){
                alert("猜大了！");
                arr[i] = val;
            }else{
                alert("猜小了！");
                arr[i] = val;
            }
        }
        if( i == 10){
            alert("游戏结束！");
        }
        btn2.onclick = function(){
            console.log(arr);
        }
    }
</script>
</html>
````

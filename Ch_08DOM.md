### appendChild()&&insertBefore()&&removeChild()
<!-- 向父节点内部最后位置插入的appendChild() -->
<!-- 向特定元素之前插入的insertBefore(new,old) -->
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>demo191118</title>
    <style>
        div{
            height:400px;
            width: 1000px;
            border:1px solid red;
            margin:0 auto;
        }
        img{
            border:1px dotted blue;
        }
    </style>
</head>
<body>
    <div id = "container">
        <img src="download.png" id="img1">
    </div>
    <button id = "insertBefore">insertBefore</button>
    <button id = "removeChild">removeChild</button>
</body>
<script>
    document.body.onclick = function(){
        var imgNode = document.createElement("img");
        var container = document.getElementById("container");
        imgNode.src = "logo.png";
        var body = document.body;
        body.appendChild(imgNode);
        container.appendChild(imgNode);
        //追加子节点，parentNode.appendChild(childNode)
        // 向parentNode节点对象标记内部最后的位置添加childNode
    }
    var insertBefore = document.getElementById("insertBefore");
    var img1 = document.getElementsByTagName("img")[0];//得到集合后加索引[0]
    insertBefore.onclick=function(e){
        e.stopPropagation();//阻止事件的冒泡
        var container = document.getElementById("container");
        var img2 = document.createElement("img");
        img2.src = "logo.png";
        container.insertBefore(img2,container.firstElementChild);
    }
    var removeChild = document.getElementById("removeChild");
    removeChild.onclick = function(e){
        e.stopPropagation();
        var container = document.getElementById("container");
        var first = container.firstElementChild ;
        // container.removeChild(first);
        first.parentNode.removeChild(first);
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
    <title>demo191118</title>
    <style>
        div{
            height:400px;
            width: 1000;
            border:1px solid red;
            margin:0 auto;
        }
        img{
            border:1px dotted blue;
        }
    </style>
</head>
<body>
    <ul id = "list">
        <li>1</li>
        <li>2</li>
        <li>3</li>
    </ul>
    <button id = "insertBefore">insertBefore</button>
    <button id = "appendChild">appendChild</button>
    <button id = "removeChild">removeChild</button>
</body>
<script>
    var list = document.getElementById("list");
    var insertBefore = document.getElementById("insertBefore");
    var appendChild = document.getElementById("appendChild");
    var removeChild = document.getElementById("removeChild");
    
    appendChild.onclick = function(){
        var liNode = document.createElement("li");
        var liCount = list.children.length+1;
        liNode.innerHTML = liCount;
        list.appendChild(liNode);
    }
    
    insertBefore.onclick=function(){
        var liNode = document.createElement("li");
        liNode.innerHTML = "insertBefore";
        list.insertBefore(liNode,list.firstElementChild);
    }
    removeChild.onclick = function(){
        list.removeChild(list.firstElementChild);
    }
</script>
</html>
````
### 删除表格指定行
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>demo</title>
    <style>
        td{
            width:200px;
        }
    </style>
</head>
<body>
    <table border="1" celllspacing="0" id = "tb">
        <tr>
            <td>
                <button>点我删除行0</button>
            </td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>
                <button>点我删除行1</button>
            </td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>
                <button>点我删除行2</button>
            </td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>
                <button>点我删除行3</button>
            </td>
            <td></td>
            <td></td>
        </tr>
    </table>
</body>
<script>
var tb = document.getElementById("tb");
var btnList = tb.getElementsByTagName("button");
for (var i = 0; i < btnList.length; i++) {
    //在事件的回调函数中，获取到的是遍历结束时的i值
    // btnList[i].onclick =function(){
    //     //现阶段 变量没有块级作用域，共用一块空间
    //     console.log(i);
    // }
    // 在事件的回调函数中，this指向触发事件的DOM对象。
    btnList[i].onclick = function(){
        var trNode = this.parentNode.parentNode;
        trNode.parentNode.removeChild(trNode);
    }
}
</script>
</html>
````


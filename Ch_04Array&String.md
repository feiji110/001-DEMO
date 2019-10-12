### 字符串操作
````js
var str01 = "aabbtmdctmdc";
	var str02 = "ddeeff";
	
	//length – 返回字符串的长度，所谓字符串的长度是指其包含的字符的个数。 
	document.write('<h1>length</h1>');
	document.write(str01.length  + '</br>');
	
	//indexOf() – 返回字符串中一个子串第一处出现的索引。如果没有匹配项，返回 -1 
	document.write('<h1>indexOf()</h1>');
	document.write(str01.indexOf("aa") + '</br>');
	
	//substr() – 返回字符串的一个子串。传入参数是起始位置和截取的长度。如果没有第二个参数，就取到末尾
	document.write('<h1>substr()</h1>');
	document.write(str01.substr(1)  + '</br>');
	document.write(str01.substr(2,3)  + '</br>');

	//charAt() – 返回指定位置的字符。
	document.write('<h1>charAt()</h1>');
	document.write(str01.charAt(2)  + '</br>');

	//split() – 通过将字符串划分成子串，将一个字符串做成一个字符串数组。
	document.write('<h1>split()</h1>');
	var str03 = "aa.bb.cc"
	document.write(str03.split("."));
	console.log(str03.split(".")); //使用打印看数组结构


	//以下作为扩展

	
	//replace() – 用来查找匹配指定的字符串，返回使用新字符串代替匹配的字符串后的字符串（只替换第一个）。
	document.write('<h1>replace()</h1>');
	document.write(str01.replace('tmd','***')  + '</br>');

	//lastIndexOf() – 返回字符串中一个子串最后一处出现的索引，如果没有匹配项，返回 -1
	document.write('<h1>lastIndexOf()</h1>');
	document.write(str01.lastIndexOf('b')  + '</br>');
	
	//slice(start,end) – 提取字符串的一部分，并返回一个新字符串。两个参数，第一个为起始位置，第二个为终止位置（留头不留尾），如果没有end，就取到末尾
	document.write('<h1>slice()</h1>');
	document.write(str01.slice(1)  + '</br>');
	document.write(str01.slice(1,3)  + '</br>');
	
	//toLowerCase() – 将整个字符串转成小写字母。
	//toUpperCase() – 将整个字符串转成大写字母。 
	document.write('<h1>toLowerCase()/toUpperCase()</h1>');
	var str04 = 'aaBBcc';
	document.write(str04.toLowerCase() + '</br>');
	document.write(str04.toUpperCase() + '</br>');
	
	//转义字符，输出特殊字符,  如要输出"
	document.write('<h1>转义字符</h1>');
    document.write('\"');
````
### demo4-1
````js
//1. 定义一个帖子字符串
var msgContent = "第1条帖子这是我的第1条帖子";
//2. 截取字符串的前5个字符
var len = msgContent.length;
if (len > 5)
{
    var txt = msgContent.substr(0, 5);
    txt += "……";
    alert(txt);
} else {
    alert(msgContent);
}	
````
### 数组操作
````js
var array = [1, 2, 3, 4, 5];
console.log(array.length);

//数组长度可修改
array.length = 3;
console.log(array);

//连接数组为一个字符串
var str =  array.join("|");
console.log(typeof str);
console.log(str);

//向数组末尾增加一个元素,并返回新数组的长度
array.push(3.1415926);
console.log(array);

//删除并返回数组最后一个元素
var data = array.pop();
console.log(data);

//删除并返回数组第一个元素
var first = array.shift();
console.log(first);

//向数组的开头添加一个或更多元素，并返回新的长度
var lg = array.unshift(0);
console.log(array);
console.log(lg);

//连接两个或更多的数组，并返回结果,该方法不会改变原来的数组，而仅仅会返回被连接数组的一个副本
//concat方法中的参数可以是多个，一个数组，也可以是多个数组，也可以是基本类型的值
var newArr = array.concat([6,7,8])
console.log(newArr)

//reverse颠倒数组中元素的顺序，该方法会改变原来的数组，而不会创建新的数组
array.reverse();
console.log(array);

//arrayObject.slice(start,end)返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。
//如果没有指定end参数，那么返回从 start 到数组结束的所有元素组成的数组
var newArr = array.slice(1,3);
console.log(newArr);

// splice(index,howmany,item1,.....,itemX) 向（从）数组中添加（删除）项目，然后返回被删除的项目。
// index必需。整数，规定添加/删除项目的位置,howmany必需。要删除的项目数量。如果设置为 0，则不会删除项目。
// item1, ..., itemX可选。向数组添加的新项目
array.splice(1,2);//从第一位开始删，删两个
console.log(array);

array.splice(1,2,100);//从第一位开始删，删两个,在第一位添加 100
console.log(array);
````
### 
````html
<!DOCTYPE html>
<html>
<head>
  	<title> new document </title>
  	<meta charset="utf-8" />
  	<style type="text/css">
		a{
			color: #999;
			text-decoration: none;
		}
  	</style>
</head>

<body>
	<div style="height: 20px;"></div>
	<div id="msg">		
		<script type="text/javascript">
			//帖子数组的定义
			var msgArr = [['第2条帖子', 'a', '第2条帖子这是我的第2条帖子', '2011-02-14'],
						            ['第4条帖子', 'c', '第4条帖子这是我的第4条帖子', '2011-02-01'],
						            ['第3条帖子', 'b', '第3条帖子这是我的第3条帖子', '2011-02-23'],
						            ['第1条帖子', 'c', '第1条帖子这是我的第1条帖子', '2011-02-08'],
						            ['第5条帖子', 'b', '第5条帖子这是我的第5条帖子', '2011-02-18']];
			//1. 生成表格表头的函数
			function createHeader() {
				document.write('<table align="center" cellpadding="20px" border="1px" cellspacing="0">');
				document.write('<tr>');
				document.write('<th>标题</th>');
				document.write('<th>发贴人</th>');
				document.write('<th>帖子概览</th>');
				document.write('<th>发贴时间</th>');
				document.write('</tr>');
			} //end of createHeader()
			//2. 把一个数组中的元素，循环遍历到表格中
			function createContent(msgArr) {
				for (var i=0, len=msgArr.length; i<len; ++i)
				{
					//插入“<tr>”标签
					document.write('<tr>');
					//循环遍历每一行中的每一个单元格
					for (var j=0; j<4; ++j)
					{
						//插入“<td>"标签
						document.write('<td>');
						//插入单元格内容
						//若输出帖子内容，则只输出前5个字符
						if (2 == j && msgArr[i][j].length > 5)
						{
							var content = msgArr[i][j].substr(0, 5);
							document.write(content);
							document.write('……');
						} else {
							document.write(msgArr[i][j]);
						}
						//插入“</td>”标签
						document.write('</td>');
					}
					//插入“</tr>”标签
					document.write('</tr>');
				}
			} //end of createContent()
			//3. 生成表格的结束标志符“</table>”
			function createFooter() {
				document.write('</table>');
			} //end of createFooter()
			//4. 输出表格
			function printTable()
			{
				createHeader();
				createContent(msgArr);
				createFooter();
			}
		printTable();
		</script>
	</div>

 </body>
</html>
````
### forEach()用法
````js
var arr=[1,2,3,4,5,6];
arr.forEach(function(value,index,arr1){
     //分别对应：数组元素，元素的索引，数组本身
    document.write(arr1[index]+',');
    document.write('索引值为'+index+'的元素是:'+value+'<br>');
})
arr.forEach(function(v){
    //其中的v就是数组的值 123456
    document.write(v+"<br>");
})
//forEach()函数从头到尾把数组遍历一遍。有三个参数分别是：
//数组元素，元素的索引，数组本身（如果是一个参数就是数组元素，也就是数组的值。 
````

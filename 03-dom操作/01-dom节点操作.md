### 1.获取事件源的方式(DOM节点的获取)
``` html
var div1 = document.getElementById('box1'); //方式一:通过id 获取单个标签
var arr1 = docuemnt.getElementsByTagName("div");  //方式二: 通过标签名 获得 标签数组,所以有s
var arr2 = document.getElementsByClassName("hehe"); //方式三: 通过 类名 获得 标签数组,所有有s
```
### 2.绑定事件的方式
方式一: 直接绑定匿名函数
``` html
<div id="box1"></div>

<script type="text/javascript">
	var div1 = document.getElementById("box1");
	//绑定事件的第一种方式
	div1.onclick = function() {
		alert("我是弹出的内容");
	};
</script>
```
### 3.事件驱动程序
* 在js里写属性值时,要用引号`''`
* 在js里写属性名时,时`backgroundColor`,不是css里的`background-color`
## DOM的介绍
DOM：Document Object Model，文档对象模型.DOM为文档提供了结构化表示,并定义了如何通过脚本来访问文档结构.目的其实就是为了能让js操作html元素而制定的一个规范
DOM就是由节点组成的
### DOM树(一切都是节点)
* 元素节点: HTML 标签
* 文本节点: 标签中的文字(比如标签之间的空格,换行)
* 属性节点: 标签的属性
#### DOM可以做什么
* 找对象(元素节点)
* 设置元素的属性值
* 设置元素的样式
* 动态创建和删除元素
* 事件的触发相应: 事件源,事件,事件的驱动程序
### DOM访问关系的获取
#### 获取父节点
调用者就是节点.一个节点只有一个父节点,调用方式就是
``` html
节点.parentNode;
```
#### 获取兄弟节点
##### 1.下一个节点|下一个元素节点
Sibling的中文是: 兄弟
(1) 节点.nextSibling
(2) 节点.nextElementSibling
``` html
兼容: 下一个兄弟节点 = 节点.nextElementSibling || 节点.nextSibling;
```
##### 2.前一个节点|前一个元素节点:
pervious的中文是: 前一个
(1) 节点.previouSibling
(2) 节点.previousElementSibling
``` html
兼容: 前一个兄弟节点 = 节点.nextElementSibling || 节点.nextSibling;
```
#### 获取单个的子节点
##### 1.第一个子节点| 第一个元素子节点
(1) 节点.firstChild
(2) 节点.firstElementChild
``` html
兼容: 第一个子元素节点 = 节点.nextElementSibling || 节点.nextSibling;
```
##### 2.最后一个子节点| 最后一个子元素节点
(1) 节点.lastChild
(2) 节点.lastElementChild
``` html
兼容: 最后一个子元素节点 = 节点.nextElementSibling || 节点.nextSibling;
```
总结 (1)
* 火狐,谷歌,IE9+版本: (包括标签,空文档和换行节点)
* IE678版本:指子元素节点(标签)
(2)
* 火狐,谷歌,IE9+版本:都指的是子元素节点(标签)
#### 获取所有的子节点
(1) childNodes: 标准属性.返回的是指定元素的子节点的集合(包括元素节点,所有属性,文本节点)
* 火狐 谷歌等高等版本把换行也看做是子节点
用法:
``` html
子节点数组 = 父节点.childNodes; //获取所有节点
```
(2) children: 非标准属性.返回的是指定元素的子元素节点的集合 
* 它只返回HTML节点,甚至不返回文本节点
* 在IE6/7/8中包含注释节点(在IE678中,注释节点不要写在里面)
用法:
``` html
子节点数组 = 父节点.children; //获取所有节点 用的最多
```
### nodeType 属性
* nodeType == 1 表示的是元素节点(标签) 注意:元素就是标签
* nodeType == 2 属性节点
* nodeType == 3 文本节点
* nodeType == 8 注释节点
### DOM节点的操作
#### 创建节点
``` html
新的标签(元素节点) = document.createElement("标签名");
```
#### 插入节点
``` html
(1) 父节点.appendChild(新的子节点);
1. 父节点的最后插入一个新的子节点
```
``` html
(2) 父节点.insertBefore(新的子节点,作为参考的子节点)
1. 在参考节点前插入一个新的节点
2. 如果参考节点为null,name他将在父节点里面的最后插入一个子节点
```
#### 删除节点
``` html
父节点.removeChild(子节点);
用父节点删除子节点.必须要指定是删除哪个子节点.
```
``` html
node1.parentNode.removeChild(node1);
删除自己这个节点
```
#### 复制节点(克隆节点)
``` html
要复制的节点.cloneNode(); // 括号里不带参数和带从参数false,效果是一样的,只复制节点本身,不复制子节点
要复制的节点.cloneNode(true); // 带参数true:既复制节点本身,也复制其所有的子节点
```
### 设置节点的属性
#### 1.获取节点的属性
方式1:
``` html
元素节点.属性
元素节点[属性]
```
方式2:
``` html
元素节点.getAttribute('属性名称');
```
#### 2.设置节点的属性值
方式1: (设置节点的属性值)
``` html
maNode.src = "images/2.jpg"; //修改src的属性值
myNode.className = "image2-box"; //修改class的name
```
方式2:
``` html
元素节点.setAttribute(属性名,新的属性值);
```
#### 3.删除节点的属性
``` html
元素节点.removeAttribute(属性名);
```
总结:
获取节点的属性值和设置节点的属性值,都有两种方式,但这两种方式有区别
* 方式一的`元素节点.属性`和`元素节点[属性]`:绑定的属性值不会出现在标签上
* 方式二的`get/set/removeAttribute`:绑定的属性值会出现在标签上
### DOM对象的属性
DOM 对象的属性和 HTML 的标签属性几乎是一致的。例如：src、title、className、href 等。
#### innerHTML 和 innerText的区别
* value:标签的value属性
* innerHTML: 双闭合标签里面的内容(识别标签).  会修改标签本身
* innerText: 双闭合标签里面的内容(不识别标签).  不会修改标签本身
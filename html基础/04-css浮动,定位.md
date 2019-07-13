##文档流
* 块状标签独占一行
* 行内元素可以同一行显示,如果不够会自动换行
* 自上而下的展示
##浮动
> 浮动指的是使元素脱离原来的文本流,在父元素中浮动起来
* 浮动使用float属性.
* 可选值:
    * none:不浮动
    * left: 向左浮动
    * right: 向右浮动
* 块状元素和行内元素都可以浮动,当一个行内元素浮动以后将会自动变为一个块状元素.
* 当一个块状元素浮动以后,宽度会默认被内容撑开,所以当漂浮一个块级元素时我们都会为其指定一个宽度.
####浮动的表现形式
* 当一个元素浮动以后,其下方的元素会上移.元素中的内容将会围绕在元素的周围.
* 浮动会使元素完全脱离文本流,也就是不在文档中再占用位置
* 元素设置浮动以后,会一直向上漂浮直到遇到父元素的边界或其他浮动元素.
* 元素浮动以后即完全脱离文档流,这时不会再影响父元素的高度.也就是浮动元素不会撑开父元素.
* 浮动元素默认会变为块元素,即使设置display:inline以后其依然是个块元素.
####浮动的影响
* 如果子类元素设置了浮动,而父类元素没有设置高度,或者高度比子类元素小,那么子类元素脱离了文档流,就无法把父类盒子撑开,那么整个文档的结构将受到破坏.
* 清除浮动的影响(父类高度塌陷):
     1.给父类 指定足够的高度
     2.给父类盒子 设置overflow:hidden;
     3.在浮动元素的最后面追加一个空的div,设置clear:both即可清除浮动的影响.
* 因为浮动会对文档流造成影响,所以能用流式布局 就不要使用浮动.
* > 在同一个父类元素里边,要浮动 都浮动
* 补充:
    1.display:inline-block 标签的换行符会被显示为空格
    2.foat:right 会改变标签的前后顺序.
``` html
<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
		<style>
			*{
				margin: 0;
				padding: 0;
			}
			.header{
				width: 100%;
				height: 100px;
				background-color: green;
			}
			.content{
				width: 100%;
				/*height: 500px;*/
				background-color: pink;
			}
			/*同级要浮动，都浮动*/
			.content .aside{
				float:left;
				width: 200px;
				height: 300px;
				background-color:red;
			}
			.content .main{
				float:left;
				width: 800px;
				height:900px;
				background-color: gray;
			}
			.footer{
				width: 100%;
				height: 100px;
				background-color: black;
			}
			/*不允许当前元素左右出现浮动元素  这样可以清除浮动的影响*/
			.clr{
				clear: both;
			}
		</style>
	</head>
	<body>
		<div class="header">
			
		</div>
		<div class="content">
			<div class="aside">
				
			</div>
			<div class="main">
				
			</div>
			<div class="clr"></div>
		</div>
		<div class="footer">
			
		</div>
	</body>
	</html>
```
##定位
> 通过position属性可以实现元素的定位.元素定位以后,需要通过设置left和top值相对元素定位
* position属性可以把一个元素放置网页中的任何位置.
* 可选值:
    * static 默认
    * relative 相对定位
    * absolute 绝对定位
    * fixed 固定定位
* relative 相对定位.相对元素本身的位置定位.
    * 每个元素在页面的文档流中都有一个自然位置.相对于这个位置对元素进行移动就称为相对定位,周围的元素完全不手此影响.
    * 当开启了相对定位后,可以使用top,right,bottom,left 4个属性对元素进行定位.
    * 如果不设置元素的偏移量,元素位置不会发生改变.
    * 相对定位不会使元素脱离文本流,元素在文本流中的位置不会改变.
    * 相对定位不会改变元素原来的特性
    * 相对定位会使元素的层级提升,使元素可以覆盖文本流中的元素
``` html
.d1{
		position: relative;
		left: 100px;
		top: 100px;
		width: 200px;
		height: 200px;
		background-color: green;
	}
```
* absolute 绝对定位指使元素相对于html元素或离他最近的祖先定位元素进行定位.
    * 当开启了绝对定位以后,可以使用top/left/right/bottom四个属性对元素进行定位
    * 绝对定位会使元素完全脱离文本流.
    * 绝对定位的块元素的宽度会被其内容撑开.
    * `绝对定位会使行内元素变成块状元素`
    * `一般使用绝对定位时会同时为其父元素指定一个相对定位,以确保元素可以相对于父元素进行定位`
``` html
.d1{
		/*有绝对的事情吗？绝对的值必须有参照物*/
		/*如何才能既保证父类有定位元素 而且父类不会再原来的位置偏移*/
		/*子绝父相*/
		position: relative;
		left: 0;
		top: 0;
	/*	left: 100px;
		top: 100px;*/
		margin-left: 100px;
		width:400px;
		height:400px;
		background-color: green;
	}
	.d11{
		position: absolute;
		left: 100px;
		top: 100px;
		width:150px;
		height: 150px;
		background-color: red;
	}

	<div class="d1">
		<div class="d11">
			
		</div>
	</div>
```
* fixed 固定定位.元素会被锁定在屏幕的某个位置上,当访问者滚动网页时,固定元素会在屏幕上保持不动
    * 固定定位不占据原来的位置,会脱标.
    * 给元素设置固定定位之后,元素位置从浏览器左上角出发
    * 可以将行内元素转换为行内块元素
``` html
.zx{
			position: fixed;
			right: 100px;
			bottom: 200px;
			width: 200px;
			height: 200px;
			background-color: red;
		}

	<a class="zx" href="#">
		w shi a
	</a>
```
* z-index 当元素开启定位以后就可以设置z-index这个属性.默认是0 值越大,越靠上.
    * z-index 可以指定一个整数作为参数,值越大元素显示的优先级越高,也就是z-index值较大的元素会显示在网页的最上层.
``` html
.d1,.d2,.d3{
		position: fixed;
		left: 0;
		top:0px;
		width: 200px;
		height: 200px;
		background-color: green;
	}
	.d1{
		z-index: 9;
	}
	.d2{
		left:30px;
		top: 30px;
		background-color: blue;
		z-index:2;
	}
	.d3{
		left: 80px;
		top: 80px;
		background-color: red;
		z-index: 0;
	}


	<div class="d1">
		d1
	</div>
	<div class="d2">
		d2
	</div>
	<div class="d3">
		d3
	</div>
```
##规避脱标流
> 经验: 一般布局采用标准流,如果布局实现不了用浮动,定位一般用于解决小范围的某个标签的位置.
* 能用标准流(没有脱标)解决就不用浮动
* 解决不了就考虑用浮动(页面布局类型"不完全脱标")
* 浮动解决不了用定位(小图标,完全脱标,不影响内容)
##css
> 全称层叠样式表,用于实现页面的样式层叠,简单来说就是一个元素可以多次对他设置同一个样式,但是具体生效看哪一次权重最高
##书写位置
* 行内样式```<p style="color:red;font-size:24px;">这是一个p标签</p>```
* 内部样式```<style>p{color:red;}</style;>```
* 外部引入```<link rel="stylesheet" href="style.css">
* 区别
    * 行内样式 严重耦合 用的很少
    * 内部样式 测试使用 当前页面的样式只能当前页面使用
    * 外部样式 上线使用 多个页面可以复用样式
``` html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<title>Document</title>
		<!-- 外链,外部引入方式 -->
		<!-- 引入路径规则 和 图片引入规则一样 -->
		<link rel="stylesheet" href="style.css" />
		<!-- 内部书写 -->
		<style>
			/* 语法: 
    选择器{
        样式名:样式值;
        样式名:样式值;
    } */
			/* 分号不能省略 */
			p {
				color: orange;
				font-size: 16px;
			}
		</style>
	</head>
	<body>
		<!-- 行内样式语法 -->
		<!-- style="样式名:样式值;样式名:样式值;" -->
		<!-- 分号不能省略 -->
		<p style="color: red; font-size: 24px;">我是一个P标签</p>
		<p>我是内部样式的p标签</p>
	</body>
</html>
```
##选择器
* 简单选择器
    * 标签选择器
    * id选择器
    * class选择器
``` html
/* 标签选择器 */
        p{
            color：red；
        }
        /*id选择器*/
		#h3{
			color: orange;
		}
        /* class选择器 */
        .header{
            color:blue;
        }
```
* 复杂选择器
    * 交集选择器	没有空格 .title.text p.title
    * 并集选择器	同时选中多个 逗号隔开
    * 后代选择器	中间是空格
    * 通配符选择器	选中所有标签
``` html
/*标签p 和.p1的交集*/
p.p1 {
	color: red;
}
.p2.danger {
	color: blue;
}
/*并集选择器 都被选中*/
.p1,
.p2 {
	font-size: 30px;
}
/*后代选择器 空格*/
.p3 a {
	color: red;
}
/** 通配符 选择所有标签*/
* {
	/*background-color: pink;*/
}
```
##css继承性
字体相关 文本相关的一些属性(text-align line-height text-indent)
[css中可以和不可以继承的属性总结](https://www.cnblogs.com/thislbq/p/5882105.html)
##css层叠性
* 样式冲突,必然只有一个样式生效
##css权重问题
* 行内样式>id选择器>class选择器>标签选中器
* 复杂选择器权重计算-行内样式1000>id选择 100 >class选择 10 >标签 1 > 通配符/继承属性0
* 如果两个选择器是一样的,遵循就近原则
* 如果写了相同的选择器,希望某个选择器权重更高,添加class即可
##css单位
* px 像素单位
* em 基于当前字体的倍数: text-indent:2em;首行缩进2字符;
* 颜色-预定义颜色: blue yellow pink等-十六进制:每两位表示一种颜色的深度 分别表示red green blue;比如: #ff00ff
``` html
- rgb:   rgb(0,0,255) ==> 绿色 ； rgb和十六进制是可以互换的。
- rgba:  rgba(0,0,255,0.5) ==> 跟rgb一样，a是透明度：0~1； 0.5==> .5
```
##css常用属性
| 属性名称  |   属性作用 |  值  |
| ---- |  :--: | :--:  | :--:  |
| width/height  |   宽高 |  px百分比em等  | 
| background-color  |   背景颜色 |  color  | 
|color|字体颜色|color|
|font-size|字体大小|px em 等|
|text-align|文字对齐方式|center left right|
|text-indent|首行缩进|px em 等|
|font-family|字体|围绕雅黑 Microsoft YaHei、黑体 SimHei、Arial 等|
|font-weight|字体加粗|100-900.加粗700-900/bolder lighter normal|
|font-style|字体样式|ltalic 斜体/normal正常|
|line-height|行高|单位:px/倍数/百分比;设置文字的行间距,单行文字垂直居中:行高=父类盒子高度|
|font|字体缩写|font:italic border 20px/1.2 'Arial','Microsoft YaHei'|
##背景图片
|属性名称|属性作用|值|
|----|----|----|
|background-color|背景图片颜色|color|
|background-image|背景图片|ur('1.png');|
|background-repeat|平铺方式|repeat,no-repeat,repeat-x/y|
|background-position|图片位置|left,right,top,bottom,center|
|background-attachment|背景滚动|scscroll,fixld(注意,基于body的定位)|
|background|简写(顺序不能错)|background:color url() no-repeat center center fixed|
``` html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<title>Document</title>
		<style>
			body {
				background-image: url("img/banner.jpg");
				background-repeat: no-repeat;
				/* 第一个值 水平方向位置left/right/center 第二 垂直方向位置 top/center/bottom */
				background-position: left top;
				/* 垂直方向不写 默认为center */
				/*是否跟最滚动*/
				background-attachment: fixed;
			}
			.d1 {
				width: 100%;
				height: 400px;
				/*background-color: green;*/
				/*background-image: url('img/bf.png');*/
				/*background-repeat: no-repeat;*/
				/*center 默认的是x轴  y轴默认居中*/
				/*跟数学的坐标系是不同的，x轴为正 ，y轴向下正 */
				/*background-position: -35px 30%;*/
				background: green url("img/bf.png") no-repeat right 200px fixed;
				/*如果设置了fixed 那么背景图片的位置将会基于body*/
				/*background-attachment:fixed;*/
				/*精灵图片 雪碧图 做案例的时候再补充*/
				background-color: purple;
			}
			.d2 {
				widows: 100%;
				height: 1000px;
				background-color: pink;
				/*透明度 ： 0~1  */
				opacity: 0.5;
			}
		</style>
	</head>
	<body>
		<!-- div 是一个标签，不表示任何的内容，没有自带样式。只是用于划分结构 -->
		<div class="d1"></div>
		<div class="d2"></div>
	</body>
</html>
```
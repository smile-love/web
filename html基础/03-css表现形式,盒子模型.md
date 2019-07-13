##标签的表现形式
 > 块状标签 :`p h1~h6标签 div ul li ol table hr br dl dt dd`.
  `display:block` 块状元素 设置宽高有效 会自动换行
 > 行内标签 :`span a del ins em  strong i b`.
  `display:inline`行内元素 设置宽高无效 不会自动换行(同一行展示)
 > 行内块标签 : `img button input`.
  `display:inline-block`行内块元素 设置宽高有效 同行展示不会自动换行
##盒子模型
> css处理网页时,它认为每个元素都包含在一个不可见的盒子里,包含content(内容区域)、padding（内边距）、border（边框）、margin（外边距,盒子与盒子的距离）
  所有页面的元素都可以看成是一个盒子,占据一定的页面空间
* padding
    * `padding:10px 20px 30px 40px` 这样会设置元素的上,右,下,左四个方向的内边距.
    * `padding:10px 20px 30px` 分别指定上、左右、下四个方向的内边距
    * `padding:10px 20px`分别指定上下,左右四个方向的内边距
    * `padding:10px`同时指定4个方向
    * `padding-top,padding-left/right/bottom`分别指定4个方向的内边距
* margin
    * 用法和padding类似,提供四个方向的margin-top/right/bottom/left.
    * margin:xxx auto;可以使元素居中.
    * 嵌套崩塌:两个盒子发生嵌套的时候,给子类设置margin会给父类造成一种崩塌现象,子类的margin-top没有效果,而直接作用到父类
    * 解决方案:
        1.父类 `overflow:hidden;`
        2.父类 设置极小的`padding`
    * 重叠:如果垂直两个块状元素同时设置了margin-bottom和margin-top,那么这两个值将会发生重叠,不会累加,哪个值大用哪个.
    * margin-top/margin-bottom 对于行内元素无效
``` html
<style>
    .d2{
		width:200px;
		height:200px;
		background-color: red;
		/*margin: 100px;
		margin-top: 200px;*/
		/*d2将会左右居中*/
		margin: 100px auto;
	}
</style>
	<!-- ======================= -->
	<!-- 当两个盒子发生嵌套的时候，给子类设置maring会给父类造成一种崩塌现象，子类的margin-top没有效果，而直接作用到父类 -->
	<!-- 解决方案： 1. 父类  overflow: hidden
                            字面意思 超出部分隐藏
                            用在这里 可以解决嵌套崩塌
			   2. 父类 设置极小的padding -->
	<div class="box">
		<div class="inner-box">
			
		</div>
	</div>

	<hr>
	
	<!-- 如果垂直两个块状元素同时设置了margin-bottom和margin-top,那么这两个值将会发生重叠,不会累加，哪个值大用哪个 -->
	<div class="box2">
		
	</div>
	<div class="box3">
		
	</div>	
```
* border
    * 可以再元素周围创建边框,边框是元素可见框的最外部.
    * border:1px solid red 分别指定了边框的宽度,颜色和样式,是一种缩写:border-width,border-style,border-color
    * `border-style:none(默认)/dashed(虚线)/dotted(点)/solid(实线)/double(双实线)`
    * 可以单独设置某一条边框:`border-right:20px solid blue;`
``` html
<style>
    .d1{
		width: 200px;
		height:200px;
		background-color: green;
		/*简写属性*/
		/*border: 10px solid red;*/
		border-width: 10px;
		border-style: solid;
		border-color: red;
		/*右边单独添加20像素*/
		border-right: 20px solid blue;
	}
</style>
```
* 影响盒子大小的因素
    * border
    * padding 特殊:继承的盒子在父盒子宽度范围内,padding值不会影响该盒子大小
* display 我们可以通过修改display赖修改元素的性质.
    * block: 设置元素为块元素
    * inline: 设置为行内
    * inline-block: 设置为行内块元素
    * none: 隐藏元素
        * 转换的必要性:比如可以把a标签转换为块状元素,进而实现一个按钮的样式.
* visibility和display不同,使用visibility隐藏一个元素,隐藏后其在文档中所占的位置依然保持,不会被其他元素覆盖
``` html
<style>
    .baidu{
			/*display 可以改变元素的表现形式*/
			display: inline-block;
			width:300px;
			height:300px;
			background-color: pink;
	}
	.p1{
            /* 使元素消失 */
			/*display:none;*/ 
            /* 使元素隐藏 */
			visibility:hidden; 
	}
</style>
```
* overflow 相关标签里面的内容超出了样式的宽度和高度时如何处理
    * visible:默认值
    * scroll:添加滚动条
    * auto:根据需要添加滚动条
    * hidden:隐藏超出盒子的内容 
``` html
<style>
        .d1{
			width: 200px;
			height: 200px;
			background-color: green;
			overflow: auto;
			/*overflow: scroll;
			overflow: hidden;*/
		}
</style>
```

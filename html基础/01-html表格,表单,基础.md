##html基础
####html是一种超文本标记语言
* 它不是一个编程语言,而是一个标记语言
* >超文本 是指单个网站内或网站之间将网页彼此连接的链接.
* html由结构 表现 行为构成
    * 结构 指的就是用html标签控制网页的结构
    * 表现 指的就是用css控制网页的样式
    * 行为 指的就是用javascript(js)控制网页的交互行为
##html骨架
* \<html\>
网页的根节点,一个网页只能有一个根标签,其余所有内容都应该写在html内
*  \<doctype html\>
    告诉浏览器以html5的标准去解析页面 默认
*  ```<html lang="en">```
    * 属性作用 声明语言环境 en  
    * 标签名 标签的属性(可以有多个属性)(属性名等于属性值)
* ```<head></head>``` 给浏览器识别用的,辅助浏览器解析页面,并不会在页面当中显示
    * \<meta> 标签(设置网页的元数据)
        * \<charset=utf-8> 指定字符集编码utf-8(优化后  的全球码)
        * [字符集编码介绍](http://www.ruanyifeng.com)
        * 网站的关键词,用于搜索引擎优化的,用于设置关键字\ <meta name="keywords"   content="河南郑州不凡学院开设UI设计培训课程"/>
        * 网站的描述信息,用于设置描述信息\ <meta name="description"   content="不凡学院,郑州UI培训,河南郑州UI设计培训"/>
          网站的关键词,用于搜索引擎优化的
        * \<title> 设置页面标题,在浏览器头部tab当中展示
    * \<body> 标签 设置网页主体,网页中所展示的内容都在body标签中
        * 多个空格和换行都会被当做一个空格处理
##常见标签
* ```<div></div>```会自动换行,多用于布局
* ```<span></span>```不会自动换行,多用于照顾某些特殊字符
* ```<h1>~<h6>``` 标题标签. 在html中一共有6级标题. h1是最大的标题,一般在页面中只能出现一次
* ```<p>``` 段落标签
* ```<br/>``` 换行标签
* ```<hr/>``` 水平换行标签
* ```<img src="" alt="sorry">``` 图片img标签
    * src 图片路径
    * alt 图片未找到时,显示的内容
    * 图片格式 jpg.png.gif.svg
* 相对路径
    * 同一级目录 直接引用 bf.png
    * 下级目录 img/bf.png
    * 上级目录 ../  ../bf.png
    * 多层 ../../(上一级的上一级)
* 绝对路径
    * 本地绝对路径 比如:H:/html+css课程/01-html/mydev/bf.png
    * 网络路径
``` html
<!-- 本地绝对路径 -->
<img src="H:/html+css课程/01-html/mydev/bf.png" alt="sorry,图片未找到">
<!-- 网络路径 -->
<img src="https://gss2.bdstatic.com/9fo3dSag_xI4khGkpoWK1HF6hhy/baike/w%3D268%3Bg%3D0/sign=586984b5572c11dfded1b8255b1c05ed/bd3eb13533fa828b9caedeb5fd1f4134960a5ad2.jpg" alt="sorry,图片未找到">

<!-- 相对路径,相对当前文件所在的目录 -->
<!-- 同级目录 -->
<img src="bf.png" alt="sorry,图片未找到">
<!-- 下级目录 -->
<img src="img/bf.png" alt="sorry,图片未找到">
<!-- 上一级目录 -->
<img src="../bf.png" alt="sorry,图片未找到">

<!-- alt 属性 用来表示 图片未找到时 所显示的内容 -->
```
* ```<a>```超链接,可以跳转到其他页面
    * ```href``` 跳转的地址
    * ```target:_self``` 默认 当前页面跳转
    * ```target:_blank``` 新的窗口打开
``` html
<!-- 当前窗口跳转 -->
<a href="https://www.baidu.com/">百度</a>
<a target="_self"  href="https://www.baidu.com/">百度</a>
<!-- 新窗口跳转 -->
<a target="_blank"  href="https://www.baidu.com/">百度</a>
<!-- 点击图片跳转 -->
<a href="https://www.baidu.com/">
    <img src="bf.png" alt="sorry,图片未找到">
</a>
```
* 列表标签
    * ul>li 无序裂变
        * 开发常用
        * list-style:none 去掉前边默认的圆点,自己实现样式
    * ol>li 有序列表
    * dl,dt,dd 自定义列表
``` html
<dt>
		<dl>第一章</dl>
			<dd>美食</dd>
			<dd>箱包</dd>
		<dl>第二章</dl>
			<dd>电脑</dd>
			<dd>手机</dd>
	</dt>
```
* 字体标签
    * 斜体/加粗 ```<em><strong>``` 
    * 斜体/加粗 ```<i><b>```单纯的表示 斜体加粗没有语义化
    * 上标/下标 ```<sup>``` ```<sub>```比如:```5<sup>2</sup>``` ```H<sub>2</sub>o```
    * 下划线/删除线 ```<ins>``` ```<del>```
* 转义字符
    * 空格 ```&nbsp; &#160;```
    * 小于号 ```&lt; 7#60;```
    * 大于号 ```&gt; &#62;```
##html基本规范(语法规范)
* html 不区分大小写,但是尽量使用小写
* html 的注释不能嵌套(注释是给代码加说明,不能在页面中展示)
* html 的标签必须完整,明明不是成对的,即使浏览器能解析,但是是错误的!
* html 标签是可以嵌套的
* 标签的属性必须加双引号""
##表格
* ```<table></table>```
    * align left|center|right 表格的位置
    * border 表格边框 同时为td(单元格)生成边框
    * bgcolor 表格背景色
    * cellspacing 单元格与单元格之间的距离
    * cellpadding 文字与单元格之间的距离
* ```<tr></tr>``` 表格的每一行
    * align left|center|right 文字对齐方式
    * bgc 当前行的背景色
* ```<th></th>```
* ```<td></td>```
    * colspan 单元格所占据的列
    * rowspan 单元格所占据的行
* ```<caption>``` 课程表
``` html
<table bgcolor="orange" cellspacing="20" cellpadding="10" border="5">
        <!-- 表格标题 -->
		<caption>课程表</caption>
		<tr>
			<th>周一</th>
			<th>周二</th>
			<th>周三</th>
			<th>周四</th>
		</tr>
		<tr>
			<td rowspan="2">语文</td>
			<td colspan="2">数学</td>
			<!-- <td>语文</td> -->
			<td>体育</td>
		</tr>
		<tr>
			<!-- <td>语文</td> -->
			<td>数学</td>
			<td>语文</td>
			<td>体育</td>
		</tr>
	</table>
``` 
##表单
* ```<from>``` 用于包括输入框,提交数据
    * action 提交的地址,暂时不用理解
    * method 提交数据的方法 get/post 如果不写,默认是get方式
* ```<input>``` 表单输入框,根据type的类型,表现不同的形式
    * type:text 必须 单行文本输入框
    * name: 当前表单的名称 目前必须要有,因为提交的时候后台   程序需要通过name属性获取表单的内容.
    * value:xx 当前标签的内容.value是提交的结构,如果设置了value,则是当前表单的默认值.
* ```<input>```:type:password 密码输入框
* ```<input>```:type:radio 单选
    * name必须要有,这里表明当前的单选输入框为一组
    * value 必须要有,因为单选按钮提交的结果是value的值,value 一般采用数字编码的形式显示
    * checked 默认选中
* ```<input>```:type:checkbox多选
    * name 同radio
    * value 同radio
    * checked 默认选中
* ```<select>```option 下拉框
    * name属性需要设置
    * value 每个option都要设置value
    * selected 默认选中
* ```<input>```:type:file 上传
    * 当选中的时候,实际文件并没有被上传上来
    * multiple 可以实现多选
* ```<textarea>```多行文本输入框
    * cols/rows 文本框的宽度和高度
    * name值需要设置,value指的是标签内部的内容
* ```<input>```:type:submit 提交按钮
    * value 按钮显示的内容
    * 点击后表单被提交到form.action配置的地址
* ```<lable>```用于包括输入框的头部和输入框 使之成为一体.多用于单选和多选.
* readonly 只读属性,输入框内容不能更改.
* disabled 禁用 表单的值再提交时会被舍弃.
* ```<fieldset>``` ```<legend>``` 可以实现表单的分组
* get提交
    * 参数被放到地址提交,比如: /D:/abc?username=张三&pwd=123&sex=0&experience=0
    * 不安全
    * 地址栏拼接的参数长度有限,一般是<4k
    * 一般用于获取数据
* post提交
    * 地址栏不显示提交内容,在请求体显示
    * 相对安全
    * 提交的数据量没有上限
    * 一般用于提交保存数据
``` html
<!-- action 是当前表单提交的地址 -->
	<form action="www.bufanui.com" method="get">
		<fieldset>
			<legend>基本信息</legend>
			用户名: <input type="text" readonly  name="username" value="张三"> <br>
			曾用名： <input type="text" disabled  name="oldname" value="张小三"><br>
			密码: <input type="password" name="pwd"> <br>	
			性别: 
				<label>
					男: <input type="radio" name="sex"  value="0"> 
				</label>
				<label>
					女: <input type="radio" checked  name="sex"  value="1"> <br>
				</label>
		</fieldset>
		
		<fieldset>
			<legend>补充信息</legend>
			爱好: 
			<label>
				篮球: <input type="checkbox" name="like" value="basketball">
			</label>
			<label>
				足球: <input type="checkbox" checked name="like" value="football">
			</label>
			<label>
				乒乓: <input type="checkbox" name="like" value="pingpang"><br>
			</label>

	    工作年龄: 
	    	<select name="experience">
	    		<option value="0">--无--</option>
	    		<option value="1">1年</option>
	    		<option value="2" selected>2~3年</option>
	    		<option value="3">3~5年</option>
	    	</select> <br>
    	上传头像: <input type="file" name="avatar" multiple> <br>
    	个人描述: <textarea name="desc" cols="30" rows="4">
    				我对工作有极大地热情,我喜欢写代码!
    			</textarea> <br>
		</fieldset>
				
		
    	<input type="submit" value="提交">
	</form>
```                                   


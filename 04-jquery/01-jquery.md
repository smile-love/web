## jquery
#### 入口函数
1.$(document).ready(funtion(){});
2.$(function(){}); 简写
#### 事件处理
jquery中的时间处理都是方法,原生js的事件处理是属性
#### 命名规范
1.下划线,字母,$,数字
2.但是不能以数字作为开头
jquery的两个变量: $ 和 jquery
注意:不能再使用这两个变量 方式引起冲突,什么时候使用jquery?当有其他框架中使用$造成冲突的时候使用jquery
#### js入口函数跟jquery入口函数的区别:
1.执行时间
``` html
window.onload必须等到页面内包括图片的所有元素加载完毕后才能执行.
$(document).ready()是DOM结构回执完毕后就执行,不必等到加载完毕.只加载了dom框架,对于大的图片需要时间
```
2.编写个数不同
window.onload 不能同时编写多个,如果有多个window.onload方法,只会执行一个
$(document).ready()可以同时编写多个,都可以执行 `简写:$(function(){});`
### jquery基本选择器
|选择器| 符号  |   说明 |  用法  |
|----| ---- |  ----  | ---- |
|id选择器| $('#demo')  |  选择id为demo的第一个元素 |  $('#demo').css('color','red')  | 
|类选择器| $('.d1')  |  选择所有类名为d1的元素 |  $('.d1).css()  | 
| 标签选择器 | $('div') | 选择所有div标签元素 | $('div').css() |
| 全选择器 |  $('*')  | 选择所有元素 | $('\*').css() |
| 交集选择器 |  $('.div.active')  | 选择div和active的元素 | $('.div.active').css() |
| 后代选择器 |  $('.demo .li')  | 选择demo的后代li | $('.demo .li').css() |
|子代选择器| $('.ul>.li') |  选择所有的子代元素  | $('.ul>.li').css() |
|兄弟选择器| $('.li3+li') |  li3的下一个兄弟元素  | $('.li3+li').css() |
|兄弟选择器| $('.li3~li') |  li3后面的li兄弟元素  | $('.li3~li').css() |
### 过滤选择器
| 符号 | 说明 |  用法  |
| ---- | ---- |  ----  |
| :eq(index) | 选择序号为index的元素 |  $('li:eq(1)').css()  |
| :gt(index) | 选择序号> index的元素 |  $('li:gt(2)').css()  |
| :lt(index) | 选择序号< index的元素 |  $('li:lt(2)').css()  |
| :odd(index) | 选择所有序号为奇数元素 |  $('li:odd').css() |
| :even(index) | 选择所有序号为偶数元素 |  $('li:even').css()  |
| :first | 选择匹配第一个元素 |  $('li:first').css()  |
| :last | 选择匹配最后一个元素 |  $('li:last').css()  |
### 属性选择器
| 符号 | 说明 |  用法  |
| ---- | ---- |  ----  |
| $('a[title]') | 包含title属性的元素 |  $('a[title]').css()  |
| $('a[title="你好"]') | title属性为你好 |  $('a[title="你好"]')  |
| $('a[title!="你好"]') | 有title属性,但title属性不=你好 |  $('a[title!="你好"]')  |
| $('a[title\$="院"]') | title属性以 院 结尾的 |  $('a[title$="院"]')  |
| $('a[title*="学"]') | title属性包含学这个字 |  $('a[title*="学"]')  |
| $('a[href][title="你好"]') | 既包含href又包含title=你好 |  $('a[href][title="你好"]')  |
### 筛选选择器
| 符号 | 说明 |  用法  |
| ---- | ---- |  ----  |
| find() | 查找box后代的所有p1元素 |  $('.box').find('.p1').css()  |
| children() | 所有子元素(儿子元素) |  $('.box').children().css()  |
| sibling() | 所有兄弟元素(不包括自己) |  $('.li3').sibling().css()  |
| parent() | 父元素 |  $('.d2').parent().css()  |
| eq(index) | 查找指定元素的第index个元素,索引 |  $('li').eq(3).css()  |
#### mouseover事件和mouseenter事件的区别:
* mouseover/mouseout事件,鼠标经过的时候会触发多次,每遇到一个子元素就会触发一次
* mouseenter/mouseleave 事件,鼠标经过的时候只会触发一次
## DOM对象和jquery对象相互转换
1.jquery对象转换为DOM对象
   1. $('.box')[0];
   2. $('.box').get[0];

2.DOM对象转换为jquery对象
 1. $(document) --> 把DOM对象转成了jquery对象
``` html
var btn = docuemnt.getElementById('btn');
btn --> $(btn);
```
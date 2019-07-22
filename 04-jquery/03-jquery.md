### jquery事件机制
#### 1.jquery事件的绑定
> on方式(兼容zepto(移动端类似jquery的一个库),建议使用) 
jquery1.7版本后,jquery用on统一了所有的事件处理的方法 `给匹配的元素绑定事件`
* `$(selector).on('click',function(){事件处理程序})`
#### 2.事件解绑
* off解绑on方式绑定的事件
    * `$(selector).off()` 取消所有事件
    * `$(selector).off('click')` 取消指定事件
#### 3.事件委托
``` html
$('.btn').click(function(){
    $('.box').append('<p>不凡学院</p>');
})
<!-- 想实现后来添加的元素也具备点击事件
事件委托 -->
$('.box').on('click','p',function(){
    console.log('天气很好')
})
```
#### 4.事件对象
| event.data            |   传递给事件处理程序的额外数据 |
| ----                  |  ---- |
| event.currentTarget   | 等同与this,当前DOM对象 |
| 内容  |   内容 |
| event.target          | 触发事件源,不一定===this |
| event.pageX           |  鼠标相对于文档左部边缘的位置 |
| event.type            |  事件类型:click,dbclick |
| event.keyCode         |  键盘按键代码 |
| `event.stopPropagation() `        |  `阻止事件冒泡` |
| `event.preventDefault()`         |  `阻止默认事件` |
#### 5.事件触发
* `$(selector).click()` 触发click事件
* `$(selector).trigger('click')` 方法触发指定事件 (一般不用) 
* `$(selector).triggerHandler('click')` 方法触发被选元素指定事件类型
### jquery补充
#### 1.链式编程
> 链式编程原理: `return this`; 调用`任何`一个方法都是返回了对象本身
通常情况下,只有设置操作才能把链式编程延续下去.因为获取操作的时候,会返回获取到的相应的值,无法返回this
``` html
$(this).css('width','20px').attr('class','title').css('color','red');
    `end()` 结束当前链最近的一次过滤操作,并且返回匹配元素之前的状态
```
#### 2.隐式迭代
隐式迭代的意思是: 在方法的内部会为匹配到的所有元素进行循环遍历,执行相应的方法:而不用我们再进行循环,简化操作,方便调用
通过$(this).html() 吐过获取的是多元素的值,大部分情况下返回的是第一个元素的值
#### 3.each方法
``` html
$('li').each(function(index,ele){
    <!-- ele 正在遍历的元素 dom对象 -->
    <!-- index 当前遍历的元素 的下标 -->
    if(index >= 3){
        ele.onclick = function(){
            console.log($(this).ttext());
        }
    }
})
        <!-- 大部分情况下是不需要使用each的,因为jquery隐式迭代特性,
        如果要对每个元素做不同的狐狸,这时候就用到了each方法 -->
```
#### 多库共存
`$.noConflict();`让jQuery释放对$的控制权,让其他库能够使用$符号,达到多库共存的目的
此后只能使用jquery来调用jquery提供的方法
### jquery插件 机制
#### 第三方插件
* `jquery.color.js`
    * animate()自定义动画:不支持背景的动画效果
* 日历
* 轮播
* 灯箱
* goto
* 视差
#### 任何一种jq插件的使用过程
1. 下载插件库
2. 在页面引入插件的css或者字体图片等（如果有的话）
3. 在页面引入jQuery.js
4. 在页面引入插件的js文件（core）
5. 在页面通过插件的api初始化插件 即可使用（通过查看相应的API）
`常用的插件 : 日历-- 滚动-- 表格-- 报表echar-- 树行-- 富文本--
swiper插件
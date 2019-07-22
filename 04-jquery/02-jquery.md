## DOM操作
#### 1. 样式操作 .css()
``` html
获取对应的属性值 : console.log($('.box').css('color'));
设置单个css样式 : $('.box').css('color','red')
设置多个属性样式 : $('.box').css({                 
                  backgroundColor: 'blue',
                  height: '30px'
                  }) 
```
#### 2. 属性操作 attr()
``` html
获取属性 : console.log($('.box').attr('title'))
设置属性 : $('.box').attr('title','d1')
删除属性 : $('.box').removeAttr('title')
```
#### 3. 内容操作 
``` html
添加标签 : $('.box').html('<p>我是盒子</p>')
添加内容 : innerText : $('.box').text('我是盒子')
操作表格值 : value: $('input').val('张三')   
```
#### 4.  操作类名
* `addClass()` 向被选元素添加一个或多个类名
* `removeClass()` 从被选元素删除一个或多个类名
* `toggleClass()` 对被选元素进行添加/删除类名的切换操作
* `hasClass()` 判断是否存在类名
#### 5. dom查找
* `sibling()` 除了自己以外的所有的兄弟节点
* `next()` 下一个兄弟
    * nextAll() 后面所有的兄弟
    * nextUntil() 后面所有的兄弟直到...
* `prev()` 前面的兄弟
    * prevAll 前面所有的兄弟
    * prev
* `parent()` 元素的父节点
    * parents() 所有的父节点
    * parenntUntil() 所有的父节点直到...
### jquery动画
#### 隐藏显示动画
#### 1. show 方法 : 让匹配的元素展示出来
* $(xx).show(400,function(){});
    * 第一个参数 : 动画持续时间 slow:600ms, normal: 400ms, fast: 200ms
    * 第二个参数 : 回调函数,动画执行结束后 做什么 (选填)
#### 2. hide 方法
* `$(xx).hide(400,function(){});` 
#### 3. 滑入滑出动画
* 滑入(显示): `$(xx).slideDown('slow',callback);`
    * 注意: 省略参数或者传入不合法的字符串,那么使用默认值:400ms(同样适用fadeIn/slideDown/slideUp)
* 滑出(隐藏): `$(xx).slideUp('slow',callback);`
* 滑入滑出切换动画效果 : `$(xx).slideToggle('slow',callback)`
#### 4. 淡入淡出动画
* 淡入动画效果 : `$(xx).fadeIn('slow',callback);`
* 淡出动画效果 : `$(xx).fadeOut('slow',callback);`
* 淡入但称呼切换动画效果 : `$(xx).fadeTogglee('fast',function(){});`
* 淡入改变透明度到某个值 : `$(xx).fadeTo(1000,.5);` 0全透,1全不透
#### 5. 自定义动画
* 语法: `$(xx).animate(styles,speed,easing,callback)`
    * 第一个参数表示: 要执行动画的css属性(必选)
    * 第二个参数表示: 执行动画时长(可选)
    * 第三个参数表示: 动画执行完后立即执行的回调函数(可选)
        ``` html
        $(xx).animate({
            width:200,
            color:200, 
            backgroundColor 需要安装插件
        },2000,function(){})
        ```
#### 6. 停止动画
* `stop()` 停止当前正在执行的动画
* `stop(stopAll,goToEnd)`
    * stopAll 是否全部停止,默认false `停止队列中所有的动画`
    * goToEnd 是否将停止的动画 `停止在当前动画的最后一个状态`
### jquery节点操作
#### 1. 创建节点
`var node = $('.box').html('<li\>我是<\/li>');`
#### 2. 插入节点
* `append($node或者标签字符串)`  `注意:剪切效果`
     * 作用:在被选元素内部的最后一个子元素(或内容)后面插入内容(存在或者创建出来的元素都可以)
     * 如果是给多个目标追加元素,那么方法的内部会复制多份这个元素,然后追加到多个目标里面去

* `appendTo()`
    * 作用: 把$(selector)追加到node中去
    * $(selector).appendTo(node);
* `prepend()`
    * 作用: 在元素的第一个子元素前面追加内容或节点
    * $(selector).prepend(node)
* `after()`
    * 作用: 在被选元素`(之后)`,作为兄弟元素插入内容或节点
    * $(selector).after(node)
* `before()`
    * 作用: 在被选元素`(之前)`,作为兄弟元素插入内容或节点
    * $(selector).before(node)
#### 3. 删除节点
* $(selector).remove(); 会把对象也干掉 `(重要)`
* $(selector).empty(); 被选节点里面的内容
* $(selector).html(''); 
#### 4. 复制节点
* $(selector).clone(); jq对象
### 表单 prop()
#### 1. `$(input).prop('checked')` 获取单选框或者多选框的 状态
* $(input).prop('checked',true) 如果是true 返回有这个属性 否则反之
### 尺寸位置操作(bom)
#### 1. 高度和宽度操作
>   `height() 和 width()`
    被选元素的高度 和 宽度 num 类型
    可以获取 也可以设置
``` html
console.log($('.box').width())
$('.btn1').click(function(){
    $('.box').width(500);
    $('.box').height(200);
})
```
#### 2. 坐标值操作
>   `offset()`
    作用: 获取或设置元素相对于文档的位置
    对象 可以获取left 和 top 属性
    num 类型 (设置获取)
``` html
console.log('offset.left',$('.box').fooset());
$('.btn2').click(function(){
    <!-- 设置相对于文档的位置 -->
    $('.box').offset({
        left: 300,
        top: 100
    })
})
```
#### 3. 获取相对于其最近的具有定位的父元素的位置
>   `position()`
    注意 只能获取 不能设置
    console.log($('.inner-box').position());
#### 4. 获取或者设置元素垂直方向滚动的位置
>   `scrollTop()`
    网页被卷进去的高度
``` html
$('.btn4').click(function(){
    <!-- 打印相对于网页垂直方向滚动的距离 -->
    console.log($(document.documentElement).scrollTop());
})
$('.top').click(function(){
    $(document.documentElement).animate({
        <!-- 设置卷进去的高度为0 回到顶部 -->
        scrollTop: 0
    },400)
})
```
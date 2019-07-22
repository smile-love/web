### arguments 对象
1. arguments.length; 返回的是实参的个数,只在正在使用的函数内使用
2. arguments.callee; 返回的是正在执行的函数.在使用函数递归调用时推荐用arguments.callee代替函数名本身
### 立即执行函数
``` html
function swpBindClick(){
    for(var i = 0; i < swiperPoinArr.length; i++){
        <!-- 1.onlick 这个事件是不是立即执行的 -->
        <!-- 2. click这个事件时什么时候执行的? -->
        swiperPoinAtt[i].onclick = (function(i){
            return funcction(){
                banner.setAttribute('src','img/' + bannerImgArr[i]);
                changeBannerPointer(bannerCount);
            }
        })(i);
    }
}
```
### addeventListener
#### 1.addeventListener
* 它允许给一个事件注册多个listener.
* 它提供了一种更精细的手段控制
* 它对任何DOM元素都是有效的
使用:
``` html
target.addEventListener(type,listener,iscapture);
    target:事件源
    type: 字符串,事件名称,不含'on',比如'click','mouseover'
    listener: 事件处理程序
     iscapture: 是否捕获  <!--true捕获(从外到里) false(从里到外) -->
```
#### 2.removeEventListener 移除绑定
解绑必须同是: 冒泡 或者捕获
事件类型 处理程序 冒泡捕获 必须全部一致,才能解除
`box.removeEventListener('click',foo,false)
### 定时器
#### 1.setTimeout() 延迟执行 
清除: clearTimeout()
#### 2.setInterval() 循环执行
清除: clearInterval()
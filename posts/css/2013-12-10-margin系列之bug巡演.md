## margin系列之bug巡演

### 我所知道的浏览器margin bug

* IE6浮动双margin bug；
* IE6浮动相邻元素3px bug；
* IE6/7 clear引发的margin-top bug；
* 待补充有一堆

### 为bug生为bug死为bug欲仙欲死的日子

各浏览器的实现差异或者由此而引入的错误，一直都是前端开发人员的梦魇。相信大多数的前端都为此而精疲力尽过，浏览器bug你所知有几？

### IE6浮动双倍margin bug

这当是IE6最为经典的bug之一。高大上的前端，你肯定从未与其失之交臂过。

#### 触发方式

* 元素被设置浮动
* 元素被设置与浮动方向一致的margin值

<!--more-->

来看看详细的代码吧：

#### HTML

    <div id="demo">
        <p>IE6下浮动方向上的margin值将会双倍于其指定值</p>
    </div>

#### CSS

    #demo p{
        float:left;
        margin-left:10px;
    }

#### 效果对比

![非IE6下浮动无双边距](http://demo.doyoe.com/css/margin/images/double-margin-non-ie6.png) （图一）

图一 是非IE6下的效果

![IE6下浮动双边距](http://demo.doyoe.com/css/margin/images/double-margin-on-ie6.png) （图二）

图二 是IE6下的效果


未完待续。。。



### margin系列文章：

* [margin系列之bug巡演](http://blog.doyoe.com/~posts/css/2013-12-10-margin%E7%B3%BB%E5%88%97%E4%B9%8Bbug%E5%B7%A1%E6%BC%94.md)
* [margin系列之内秀篇](http://blog.doyoe.com/~posts/css/2013-12-06-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%86%85%E7%A7%80%E7%AF%87.md)
* [margin系列之外边距折叠](http://blog.doyoe.com/~posts/css/2013-12-04-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%A4%96%E8%BE%B9%E8%B7%9D%E6%8A%98%E5%8F%A0.md)
* [margin系列之与相对偏移的异同](http://blog.doyoe.com/~posts/css/2013-12-02-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E4%B8%8E%E7%9B%B8%E5%AF%B9%E5%81%8F%E7%A7%BB%E7%9A%84%E5%BC%82%E5%90%8C.md)
* [margin系列之百分比](http://blog.doyoe.com/~posts/css/2013-11-30-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E7%99%BE%E5%88%86%E6%AF%94.md)
* [margin系列之keyword auto](http://blog.doyoe.com/~posts/css/2013-11-29-margin%E7%B3%BB%E5%88%97%E4%B9%8Bkeyword%20auto.md)
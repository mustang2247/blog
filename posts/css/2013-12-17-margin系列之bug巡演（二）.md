## margin系列之bug巡演（二）

## IE6/7 clear引发的margin-top bug

我知道，这是一个被谈及较少的bug，但我几乎可以肯定你在遇见过的同时并没有把它当成是一个bug。

### w3c关于 clear 特性的描述

设置了 `clear` 为非 `none` 值的元素，其顶部 `border` 边界 在垂直方向不允许出现在之前的浮动元素底部 `margin` 之上。

什么意思呢？用段代码来阐述：

#### HTML

    <div class="a">float:left</div>
    <div class="b">clear:left</div>

#### CSS

    .a{
        float:left;
        margin:10px;
    }
    .b{
        clear:left;
        margin-top:-30px;
    }

### margin系列文章：

* [margin系列之内秀篇（二）](http://blog.doyoe.com/~posts/css/2013-12-14-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%86%85%E7%A7%80%E7%AF%87%EF%BC%88%E4%BA%8C%EF%BC%89.md)
* [margin系列之bug巡演](http://blog.doyoe.com/~posts/css/2013-12-10-margin%E7%B3%BB%E5%88%97%E4%B9%8Bbug%E5%B7%A1%E6%BC%94.md)
* [margin系列之内秀篇](http://blog.doyoe.com/~posts/css/2013-12-06-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%86%85%E7%A7%80%E7%AF%87.md)
* [margin系列之外边距折叠](http://blog.doyoe.com/~posts/css/2013-12-04-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%A4%96%E8%BE%B9%E8%B7%9D%E6%8A%98%E5%8F%A0.md)
* [margin系列之与相对偏移的异同](http://blog.doyoe.com/~posts/css/2013-12-02-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E4%B8%8E%E7%9B%B8%E5%AF%B9%E5%81%8F%E7%A7%BB%E7%9A%84%E5%BC%82%E5%90%8C.md)
* [margin系列之百分比](http://blog.doyoe.com/~posts/css/2013-11-30-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E7%99%BE%E5%88%86%E6%AF%94.md)
* [margin系列之keyword auto](http://blog.doyoe.com/~posts/css/2013-11-29-margin%E7%B3%BB%E5%88%97%E4%B9%8Bkeyword%20auto.md)
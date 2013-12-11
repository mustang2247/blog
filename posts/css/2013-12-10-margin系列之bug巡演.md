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
* 元素在与浮动一致的方向设置margin值

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

从图一和图二的对比，我们肉眼就可以发现区别。是的，IE6下左边的外边距变成了 `margin-left` 指定值的2倍，而其它浏览器下正常，这就是经典的IE6浮动元素双倍边距bug。来看看具体的例子：`DEMO1` [IE6浮动元素双倍margin bug重现](http://demo.doyoe.com/css/margin/bug/double-margin.html)

很开心告诉你，问题要比这还更复杂一些，接着往下看。

#### 同个浮动方向的元素只有第一个元素会double margin

`double margin` 并不会发生在所有的浮动元素上，同个包含块内，在相同的浮动方向上，它只发生在第一个浮动元素上。

用代码说话：

#### HTML

    <div id="demo">
        <p>第一个float:left</p>
        <p>第二个float:left</p>
        <p>第三个float:left</p>
    </div>

CSS Code不变，加多2个浮动元素，再来看具体情况，有图有真相：

![同个浮动方向的元素只有第一个元素会double margin](http://demo.doyoe.com/css/margin/images/double-margin-only-first-child-on-ie6.png) （图三）

看到图三结果一目了然，三个 `float:left` 的元素只有第一个元素才 `double margin` 了。用个例子来终结它：`DEMO2` [同个浮动方向的元素只有第一个元素会double margin](http://demo.doyoe.com/css/margin/bug/double-margin-2.html)

#### double margin只发生在float:left时？

你觉得呢？结果当然不会是这样。在之前，我们只说过在同个浮动方向的第一个浮动元素会double margin，并没有说只有 `float:left` 才触发。

我们将 `DEMO1` 的CSS简单改改，HTML不变

#### CSS

    #demo p{
        float:right;
        margin-right:10px;
    }

结果会是怎样呢？看 `图四`：

![IE6 double margin也会发生在float:right时](http://demo.doyoe.com/css/margin/images/double-margin-on-ie6-3.png) （图四）

在图四中，我们看到右侧的外边距明显比指定值 `margin-right:10px` 要大，恩，确实，它是20px，也double了。瞧瞧：`DEMO3` [IE6 double margin也会发生在float:right时](http://demo.doyoe.com/css/margin/bug/double-margin-3.html)

那既有左浮动又有右浮动的情况将会是怎样呢？我们先来将代码呈上：

#### HTML

    <div id="demo">
        <p class="a">1 float:left</p>
        <p class="b">2 float:left</p>
        <p class="c">3 float:right</p>
        <p class="d">4 float:right</p>
    </div>
    
#### CSS

    #demo .a,#demo .b{
        float:left;
        margin-left:10px;
    }
    #demo .c,#demo .d{
        float:right;
        margin-right:10px;
    }

是的，你可能想到了，第一个左浮动元素和第一个右浮动元素都将会出现 double margin。来看 `图五`：

![既有左浮动又有右浮动的情况](http://demo.doyoe.com/css/margin/images/double-margin-on-ie6-4.png) （图五）

`DEMO4` [复杂的double margin](http://demo.doyoe.com/css/margin/bug/double-margin-4.html)

好吧，出现了2次 double margin，这看似挺复杂，其实为什么会这样，都讲得比较明白，所以应该能理解？

### double margin 不仅仅出现在margin-left/right

和大多数其它 `margin` 特性一样，double margin 也受书写模式 `writing-mode` 影响。我们在开篇所说的触发条件之一 `元素在与浮动一致的方向设置margin值` ，其实并不完全精确。当 `writing-mode` 为纵向时，会发生 double margin 的方向也相应变成了纵向。

当书写模式 `writing-mode` 纵向时，设置 `float:right` 时，会发生什么？来看代码：

#### HTML

    <div id="demo">
        <p>书写模式改变双倍margin bug方向</p>
    </div>
    
#### CSS

    #demo{
        -webkit-writing-mode:vertical-rl;
        writing-mode:tb-rl;
    }
    #demo p{
        float:right;
        margin:10px 0;
    }

CSS Code中，我们同时设置了 `margin-top/bottom` 的值都为 10px。你预期会 double 的方向是 top or bottom？不太确定？看到 `图六` 你就知道了：

![书写模式改变IE6浮动双倍margin bug方向](http://demo.doyoe.com/css/margin/images/double-margin-writing-mode-on-ie6.png) （图六）

图六清晰的验证了 `writing-mode` 会影响 double margin 的方向；并且当设置了 `float:right` 时，只有 `margin-bottom` 会 double。看看示例吧：`DEMO5` [书写模式改变IE6浮动双倍margin bug方向](http://demo.doyoe.com/css/margin/bug/double-margin-tbrl.html)

大家再猜猜，如果是 `float:left` 时， double margin 的将会是 top or bottom？

未完待续。。。



### margin系列文章：

* [margin系列之bug巡演](http://blog.doyoe.com/~posts/css/2013-12-10-margin%E7%B3%BB%E5%88%97%E4%B9%8Bbug%E5%B7%A1%E6%BC%94.md)
* [margin系列之内秀篇](http://blog.doyoe.com/~posts/css/2013-12-06-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%86%85%E7%A7%80%E7%AF%87.md)
* [margin系列之外边距折叠](http://blog.doyoe.com/~posts/css/2013-12-04-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%A4%96%E8%BE%B9%E8%B7%9D%E6%8A%98%E5%8F%A0.md)
* [margin系列之与相对偏移的异同](http://blog.doyoe.com/~posts/css/2013-12-02-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E4%B8%8E%E7%9B%B8%E5%AF%B9%E5%81%8F%E7%A7%BB%E7%9A%84%E5%BC%82%E5%90%8C.md)
* [margin系列之百分比](http://blog.doyoe.com/~posts/css/2013-11-30-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E7%99%BE%E5%88%86%E6%AF%94.md)
* [margin系列之keyword auto](http://blog.doyoe.com/~posts/css/2013-11-29-margin%E7%B3%BB%E5%88%97%E4%B9%8Bkeyword%20auto.md)
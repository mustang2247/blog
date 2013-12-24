## margin系列之bug巡演（三）

## IE8按钮margin auto居中失效Bug

你会猛然觉得，这是正解啊，因为 `button` 或者 `input type button类型` 的元素是 `inline-level` 的。

不对啊，`button` 应该是 `inline-block` 吧？

在这之前，我们似乎要先明确一些基础知识。

## 什么是 inline-level 元素？

<!--more-->

要知道 `inline-level` 元素并不等于 `inline` 元素，也就是说 `行内级元素` 与 `行内元素` 是两个不同的概念。

### `inline-level` 元素包含 `display` 值为：

* inline
* inline-block
* inline-table
* inline-flex
* other inline-*

以上情况时，元素可被称之为 `inline-level` 元素，但不都是 `inline` 元素。

## 什么是 block-level 元素？

`block-level` 指的是 `display` 值为 `block` 的元素吗？我知道不少人一直有这样的认知，不过这不完全准确。

### `block-level` 元素包含 `display` 值为：

* block
* list-item
* table
* table-*
* flex
* 如果position既不是static也不是relative、float不是none或者元素是根元素，当display:inline-table时，display的计算值为table；当display值为 inline | inline-block | run-in | table-* 时，display的计算值为block

有如上情况时的元素均被称之为 `block-lavel` 元素。需要明确的是 `block-level` 和 `block` 也不是同一个概念，所以如果你认为 `display` 值为 `list-item` 的 li 不是 块级元素，那就错了。 

看到这里，你对 `块级元素`，`块元素`，`行内级元素`，`行内元素` 这个4个概念，应该已经有了比较清晰的了解？

## margin keyword auto只能应用在常规流中的 block-level 元素上

* 当一个块级元素定义了 `position` 值为非 `static` 和 `relative` 之外的值时，margin-right/left 的计算值为0；
* 当一个块级元素定义了 `float` 值为非 `none` 之外的值时，margin-right/left 的计算值为0；
* 非块级元素的margin-right/left 的计算值为0；

计算值为0，即说明其应用使用值的意图失败。

## margin可以应用于所有元素吗？

这显然不行。准确的说：margin可以应用在除某些table-*元素和某些行内元素之外的所有元素上。

### 和margin亲近的table-*系元素

* table
* inline-table
* table-caption

除了 `display` 值为以上3种之外的 `table系` 元素，都不能应用 `margin` ，比如：th, td。

### 和margin亲近的 inline-level 元素

我之前面试的时候常会问题，行内级元素不能设置宽高对吗？大部分人会告诉我说是；然后我又会问，那为什么 `img` 可以设置宽高呢？有人会告诉我，因为 `img` 是个特殊的元素？接着我又会问题，`img` 是如何特殊的？然后，然后就没然后了，因为没声音了。

* apply
* animate

未完待续。。。

## margin系列文章：

* [margin系列之bug巡演（二）](http://blog.doyoe.com/~posts/css/2013-12-17-margin%E7%B3%BB%E5%88%97%E4%B9%8Bbug%E5%B7%A1%E6%BC%94%EF%BC%88%E4%BA%8C%EF%BC%89.md)
* [margin系列之内秀篇（二）](http://blog.doyoe.com/~posts/css/2013-12-14-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%86%85%E7%A7%80%E7%AF%87%EF%BC%88%E4%BA%8C%EF%BC%89.md)
* [margin系列之bug巡演](http://blog.doyoe.com/~posts/css/2013-12-10-margin%E7%B3%BB%E5%88%97%E4%B9%8Bbug%E5%B7%A1%E6%BC%94.md)
* [margin系列之内秀篇](http://blog.doyoe.com/~posts/css/2013-12-06-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%86%85%E7%A7%80%E7%AF%87.md)
* [margin系列之外边距折叠](http://blog.doyoe.com/~posts/css/2013-12-04-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E5%A4%96%E8%BE%B9%E8%B7%9D%E6%8A%98%E5%8F%A0.md)
* [margin系列之与相对偏移的异同](http://blog.doyoe.com/~posts/css/2013-12-02-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E4%B8%8E%E7%9B%B8%E5%AF%B9%E5%81%8F%E7%A7%BB%E7%9A%84%E5%BC%82%E5%90%8C.md)
* [margin系列之百分比](http://blog.doyoe.com/~posts/css/2013-11-30-margin%E7%B3%BB%E5%88%97%E4%B9%8B%E7%99%BE%E5%88%86%E6%AF%94.md)
* [margin系列之keyword auto](http://blog.doyoe.com/~posts/css/2013-11-29-margin%E7%B3%BB%E5%88%97%E4%B9%8Bkeyword%20auto.md)
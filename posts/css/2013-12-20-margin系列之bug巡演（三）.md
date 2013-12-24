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

## margin可以应用于所有元素吗？

这显然不行。准确的说：margin可以应用在除某些table-*元素和某些行内元素之外的所有元素上。

## 和margin亲近的table-*系标签

* table
* inline-table
* table-caption

除了 `display` 值为以上3种之外的 `table系` 标签，都不能应用 `margin` ，比如：th, td。



* apply
* animate

未完待续。。。
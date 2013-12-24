## margin系列之bug巡演（三）

## IE8按钮margin auto居中失效Bug

你会猛然觉得，这是正解啊，因为 `button` 或者 `input type button类型` 的元素是 `inline-level` 的。

不对啊，应该是 `inline-block` 吧？

在这之前，我们似乎要先明确一些基础知识。

## 什么是 block-level 元素？

<!--more-->

`block-level` 指的是 `display` 值为 `block` 的元素吗？我知道不少人一直有这样的认知，不过这不完全准确。

### `block-level` 元素包含 `display` 值为：

* block
* list-item
* table
* table-*
* flex
* 如果position既不是static也不是relative、float不是none或者元素是根元素，当display:inline-table时，display的计算值为table；当display值为 inline | inline-block | run-in | table-* 时，display的计算值为block

以上情况时的元素均被称之为 `block-lavel` 元素。需要明确的是 `block-level` 不等于 `block` ，

## margin keyword auto只能应用在常规流中的 block-level 元素上

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
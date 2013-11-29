## margin系列之keyword auto

### margin的重要性：

有个不容置疑的事，前端开发人员没有人能够忽视CSS `margin`的重要性。CSS coding时，margin的使用频率就如同呼吸般频繁，如果我可以说得夸张点的话。

margin作为CSS盒模型基本组成要素之一，是非常Basis的一个技术手段，所以我想对于它的一些基本情况应该不用太介绍了？

### margin经常被用来做什么？

* 让块元素水平居中；
* 让元素之间留有舒适的留白；
* 处理特殊的first或last，大家懂的？
* 一些布局；

<!--more-->

### 需要注意的地方：

* margin折叠；
* margin的百分比值；
* margin的auto值；
* margin和相对偏移top, right, bottom, left的异同；
* IE6浮动双margin Bug；
* IE6浮动相邻元素3px Bug；

看起来似乎有不少的知识点？恩，这些都是我们需要了解的，包括一些没有被列举出来的点。

今天要讲的其实只是其中很少的一部分，恩，标题里有：keyword auto

auto是margin的可选值之一。相信大家平时使用auto值时，最多的用法大概是 `margin: 0 auto;` 和 `margin: auto;`，恩，是的，块元素水平居中。看看代码：

```
<style>
#demo{
	width: 500px;
	margin: auto; /* 或者 margin: 0 auto; */
}
</style>

<div id="demo">
	<p>恩，我就是那个需要水平居中的家伙。</p>
</div>
```

待续。。。
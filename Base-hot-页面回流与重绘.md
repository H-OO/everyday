# 页面回流与重绘

**常识**

浏览器使用流式布局模型(Flow Based Layout)

浏览器将`HTML`解析成`DOM`、将`CSS`解析成`CSSOM`

`DOM`与`CSSOM`合并产生`Render Tree`

由于浏览器使用流式布局，对`Render Tree`的计算通常只需要遍历一次就可以完成

`table`以及其内部元素他们可能需要多次计算，开销是同等元素的三倍，尽量避免使用`table`布局

---

**回流**

会导致回流的操作

- 页面首次渲染
- 浏览器窗口大小发生改变
- 元素尺寸或位置发生改变
- 元素内容变化(文字数量或图片大小等等)
- 元素字体大小发生改变
- 添加或删除可见的`DOM`元素
- 激活伪类样式`:hover`
- 查询某些属性或调用某些方法

一些常用且会导致回流的属性和方法

- `clientWidth`、`clientHeight`、`clientTop`、`clientLeft`
- `offsetWidth`、`offsetHeight`、`offsetTop`、`offsetLeft`
- `scrollWidth`、`scrollHeight`、`scrollTop`、`scrollLeft`
- `scrollIntoView()`
- `getComputedStyle()`
- `getBoundingClientRect()` 方法返回元素的大小以及其相对于视口的位置
- `scrollTo()`
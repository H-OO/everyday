## 页面回流与重绘

**常识**

浏览器使用流式布局模型(Flow Based Layout)

浏览器将`HTML`解析成`DOM`、将`CSS`解析成`CSSOM`

`DOM`与`CSSOM`合并产生`Render Tree`

由于浏览器使用流式布局，对`Render Tree`的计算通常只需要遍历一次就可以完成

`table`以及其内部元素他们可能需要多次计算，开销是同等元素的三倍，尽量避免使用`table`布局

---

**回流 Reflow**

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

---

**重绘 Repaint**

重绘指元素样式改变但不影响它在文档流中的位置，浏览器会将新样式赋予给元素并重新绘制它的过程

---

**性能比较**

回流比重绘的代价要更高

有时仅仅回流一个元素，其父元素以及任何跟随它的元素也会产生回流

---

**现代浏览器对回流的优化**

浏览器通过维护一个队列，把所有引起回流和重绘的操作放入队列中  
如果任务数量或时间间隔达到一个阈值，浏览器会清空队列，统一进行一次回流和重绘

当访问以下属性和方法时，浏览器会立即清空队列

- `clientWidth`、`clientHeight`、`clientTop`、`clientLeft`
- `offsetWidth`、`offsetHeight`、`offsetTop`、`offsetLeft`
- `scrollWidth`、`scrollHeight`、`scrollTop`、`scrollLeft`
- `width`、`height`
- `getComputedStyle()`
- `getBoundingClientRect()`

清空的原因：队列中可能存在影响这些属性或方法返回值的操作，清空队列是为了保证获取最精确的值

---

**如何避免**

CSS

- 避免使用`table`布局
- 尽可能在`DOM`树最末端改变`class`
- 避免多层内联样式
- 动画效果应用在`position`属性值为`absolute`或`fixed`的元素上
- 避免使用css表达式，例如：calc()

JS

- 避免频繁操作样式，最好一次性重写`style`属性
- 避免频繁操作`DOM`
- 可先将元素设置`display: none`，等操作完成再显示出来，期间不会引发回流和重绘
- 避免频繁访问引发回流/重绘的属性
- 有复杂动画的元素使用绝对定位，使它脱离文档流，否则会引发父元素以及后面跟随它的元素频繁回流

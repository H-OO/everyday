# 三大家族

**家族成员**

分别如下：

|    client    |    offset    |    scroll    |
| :----------: | :----------: | :----------: |
| clientWidth  | offsetWidth  | scrollWidth  |
| clientHeight | offsetHeight | scrollHeight |
|  clientTop   |  offsetTop   |  scrollTop   |
|  clientLeft  |  offsetLeft  |  scrollLeft  |

- Element.client[Width|Height] // size = padding + content
- Element.offset[Width|Height] // size = border + padding + content
- Element.scroll[Width|Height] // size = padding + content
- Element.clientTop // 获取元素顶部边框大小
- Element.clientLeft // 获取元素左侧边框大小
- Element.offsetTop // 获取与最近一个有定位的父元素的顶部距离
- Element.offsetLeft // 获取与最近一个有定位的父元素的左侧距离
- Element.scrollTop // 获取或设置元素顶部遮挡距离
- Element.scrollLeft // 获取或设置元素左侧遮挡距离

---

**使用 scrollTop 成员的正确方式**

- 父元素需设置`overflow: hidden`
- 子元素高度大于父元素高度

注意：滚动范围 `<=` (子元素高度 - 父元素高度)，超出会自动按边界值处理

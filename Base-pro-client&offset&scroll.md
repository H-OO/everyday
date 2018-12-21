# 三大家族

**家族成员**

|    client    |    offset    |    scroll    |
| :----------: | :----------: | :----------: |
| clientWidth  | offsetWidth  | scrollWidth  |
| clientHeight | offsetHeight | scrollHeight |
|      -       |  offsetTop   |  scrollTop   |
|      -       |  offsetLeft  |  scrollLeft  |

- Element.client[Width|Height] // size = padding + content
- Element.offset[Width|Height] // size = border + padding + content
- Element.scroll[Width|Height] // size = padding + content
- Element.offsetTop // 获取与最近一个有定位的父元素的顶部距离
- Element.offsetLeft // 获取与最近一个有定位的父元素的左侧距离
- Element.scrollTop // 获取或设置
- Element.scrollLeft // 获取或设置

---

**使用 scroll 成员的正确方式**

- 父元素需设置`overflow: hidden`
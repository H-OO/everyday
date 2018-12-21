# 盒模型

**什么是盒模型**

简单来说每个 html 标签都是一个方块，这个方块又包着几个小方块

分别是：margin、border、padding、content

它们的关系是：margin 包着 border 包着 padding 包着 content

---

**盒子有多大**

- F12 检查元素 `size = margin + padding + border + content` 【mpbc】
- Element.client[Width|Height] `size = padding + content` 【pc】
- Element.offset[Width|Height] `size = padding + border + content` 【pbc】
- Element.scroll[Width|Height] `size = padding + content` 【pc】

---

**怪异盒模型**

元素设置`box-sizing: border-box`开启怪异模式

```css
div {
  /* 默认标准模式 */
  /* box-sizing: content-box; */

  /* 怪异模式 */
  box-sizing: border-box;

  margin: 10px;
  border: 10px solid #000;
  padding: 10px;
  width: 100px;
  height: 100px;
}
```

- 标准模式下: border(10x2) + padding(10x2) + content(100) = `140`
- 怪异模式下: border(10x2) + padding(10x2) + content(60) = `100`

## scrollIntoView

需求场景：移动端输入框聚焦时会调起键盘，此时可视区变小，输入框可能被遮挡

优化方法：通过监听聚焦事件，调用`Element.scrollIntoView()`方法将输入框滚动到可视区

```
Element.scrollIntoView({
  behavior: 'smooth', // instant 瞬间 | smooth 平滑 | auto 自动(默认)
  block: 'center' // start 顶部对齐 | center 居中对齐(默认) | end 底部对齐
});

Element.scrollIntoView(true); // 元素滚动到顶部与窗口顶部平齐
Element.scrollIntoView(false); // 元素滚动到顶部与窗口底部平齐
```

滚动位置以最近且设置有`overflow`样式的父元素高度作为参照

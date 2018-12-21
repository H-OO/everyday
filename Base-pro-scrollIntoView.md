# scrollIntoView

需求场景：移动端输入框聚焦时会调起键盘，此时可视区变小，输入框可能被遮挡

优化方法：通过监听聚焦事件，调用`Element.scrollIntoView()`方法将输入框滚动到可视区

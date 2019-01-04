# 继承

概念：子类继承父类的属性  
最优：需协调引用类型与相同方法共享

**继承方式**

- 原型链继承 // C.prototype = new F()
- 借用构造函数继承 // F.apply(this)
- 组合继承 // 常用 C.prototype = new F()、F.apply(this)
- 原型式继承 // Object.create
- 寄生式继承 // 增强 Object.create 返回的对象
- 寄生组合式继承 // 

---

**举个栗子**

```js
/**
 * 原型链继承
 */
function F() {
  this.obj = {};
  this.todo = function() {}
}
function C() {}
C.prototype = new F();
new C() // { obj: {}, todo: f }
// 本质：重写原型对象
// 优点：实现继承
// 缺点：1、原型包含引用类型，实例会相互影响；2、无法给父类构造函数传递参数。

/**
 * 借用构造函数继承
 */
function F() {
  this.obj = {};
  this.todo = function() {}
}
function C() {
  F.apply(this);
}
new C() // { obj: {}, todo: f }
// 本质：通过`apply|call`方法改变父类构造函数的`this`指向实现继承
// 优点：弥补原型链继承的缺陷
// 缺点：方法不能被复用

/**
 * 组合继承
 */
function F() {
  this.obj = {};
}
F.prototype.todo = function() {}
function C() {
  F.apply(this); // F构造函数第2次调用
}
C.prototype = new F(); // F构造函数第1次调用
new C()
// 本质：原型链+借用构造函数
// 优点：方法可被复用
// 缺点：F构造函数被调用了两次

/**
 * 原型式继承
 */
// 原生实现
function createNative(prototype) {
  function F() {
    this.obj = {};
  }
  F.prototype = prototype;
  return new F();
}
const prototype = {
  todo: function() {}
};
const o1 = createNative(prototype);
const o2 = createNative(prototype);
o1.todo === o2.todo // true

// ES6 Object.create
const prototype = {
  todo: function() {}
};
const o1 = Object.create(prototype, {
  name: {
    value: 'yy'
  }
});
o1.name // yy
o1.todo // f
// 缺点：原型包含引用类型，实例会相互影响

/**
 * 寄生式继承
 */
function createNative(prototype) {
  function F() {
    this.obj = {};
  }
  F.prototype = prototype;
  return new F();
}
function createP(prototype, name) {
  const o = createNative(prototype);
  // 增强
  o.name = name;
  return o;
}
const prototype = {
  todo: function() {}
};
const p = createP(prototype, 'yy');
p // { name: yy }
p.todo // f
// 优点：对原型式继承返回的对象进行增强后返回

/**
 * 寄生组合式继承
 */
function F() {
  
}
F.prototype.todo = function() {}
function C() {
  F.apply(this, arguments)
}
```

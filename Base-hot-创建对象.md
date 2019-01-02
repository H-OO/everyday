# 创建对象

**模式**

- 工厂模式
- 构造函数模式
- 原型模式
- 构造函数与原型模式 // 常用
- 动态原型模式
- 寄生构造函数模式
- 稳妥构造函数模式

---

**举个栗子**

```js
/**
 * 工厂模式
 */
function p(name, age) {
  const o = new Object();
  o.name = name;
  o.age = age;
  o.sayName = function() {
    console.log(this.name);
  }
  return o;
}
p('yy', 20) // {name: "yy", age: 20, sayName: ƒ}
// 优点：解决了创建多个相似对象的问题
// 缺点：无法识别对象类型

/**
 * 构造函数模式
 */
function P(name, age) {
  this.name = name;
  this.age = age;
  this.sayName = function() {
    console.log(this.name);
  }
}
new P('yy', 20) // {name: "yy", age: 20, sayName: ƒ}
// 优点：弥补工厂模式不能识别对象类型的缺陷
// 缺点：相同功能的方法会重复创建，不能共享

/**
 * 原型模式
 */
function P() {}
P.prototype.name = 'yy';
P.prototype.age = 20';
P.prototype.sayName = function() {
  console.log(this.name);
};
const p1 = new P(); // {name: "yy", age: 20, sayName: ƒ}
const p2 = new P(); // {name: "yy", age: 20, sayName: ƒ}
// 优点：解决构造函数模式相同方法不能共享需重复创建的问题
// 缺点：原型中定义的属性，会被所有实例共享

/**
 * 构造函数模式与原型模式
 * 【常用】
 */
function P(name, age) {
  this.name = name;
  this.age = age;
}
P.prototype.sayName = function() {
  console.log(this.name);
};
const p1 = new P('yy', 20) // {name: "yy", age: 20}
const p2 = new P('hugh', 19) // {name: "hugh", age: 19}
// p1.__proto__ {sayName: ƒ, constructor: ƒ}
// p1.__proto__ {sayName: ƒ, constructor: ƒ}
p1.__proto__ === p2.__proto__ // true
p1.sayName = p2.sayName // true
// 优点：最优解决创建多个相似对象的问题

/**
 * 动态原型模式
 */
function P(name, age) {
  this.name = name;
  this.age = age;
  // 检查其中一个方法是否存在
  if (typeof this.sayName !== 'function') {
    // 为原型增加成员
    P.prototype.sayName = function() {
      console.log(this.name);
    }
  }
}
new P('yy', 20) // {name: "yy", age: 20}
// 优点：可动态定义原型中的方法

/**
 * 寄生构造函数模式
 */
function P(name, age) {
  const o = new Object();
  o.name = name;
  o.age = age;
  o.sayName = function() {
    console.log(this.name);
  }
  return o;
}
new P('yy', 20) // {name: "yy", age: 20}
// 缺点：无法识别对象类型

/**
 * 稳妥构造函数模式
 */
function P(name, age) {
  // 私有
  const name = name;
  const age = age;
  const o = new Object();
  o.sayName = function() {
    console.log(name);
  }
  return o;
}
new P('yy', 20) // {sayName: ƒ}
// 优点：
```

# Object

**Object 方法**

- assign // 属性值为复杂类型就是浅拷贝
- create // 创建一个新对象，将原型对象替换成参数对象
- defineProperty // 修改属性的描述对象
- defineProperties // 定义多个属性的描述对象
- is // 判断两个参数是否全等
- getOwnPropertyDescriptors // 获取参数对象属性的描述对象
- setPrototypeOf // 替换对象的原型
- keys // 获取对象的属性名(不含不可枚举)
- values // 获取对象的属性值(不含不可枚举)
- entries // 获取对象的属性名与属性值

---

**实例 API ES5**

- hasOwnProperty // 判断属性是否为实例私有，也就是属性是否在构造函数中
- isPrototypeOf // 判断原型对象是否一致
- propertyIsEnumerable // 属性是否可枚举
- toLocaleString // [object Object]
- toString // [object Object]
- valueOf // self

---

**数据属性**

- value // 属性值
- writable // 是否可写
- enumerable // 是否可枚举
- configurable // 是否可删除

---

**访问器属性**

- get // 读取属性时调用的函数
- set // 设置属性时调用的函数
- enumerable // 是否可枚举
- configurable // 是否可删除

```js
const data = {
  _test: 123
};
// Vue原理
const vm = (obj, property) => {
  // defineProperty { (obj: object, prop: string, descriptor: object) => object }
  Object.defineProperty(obj, property, {
    get: function () {
      return this['_' + property]
    },
    set: function(newValue) {
      this['_' + property] = newValue;
      console.log('修改视图...');
    }
  });
  return obj;
}

const state = vm(data, 'test'); // 设置属性
console.log(state['test']); // 123
state['test'] = 'xxx'; // 重新赋值
console.log(state['test']); // xxx
```

---

**举个栗子**

```ts
const o = {
  arr: [1, 2, 3]
};

// assign { (p1: object, p2?: object, p3?: object) => object }
Object.assign({}, o) // { arr: [1, 2, 3] }

// create { (p: object) => object }
Object.create(o) // {}，原型 === o

// is { (p1: any, p2: any) => boolean }
Object.is([], []) // false

// getOwnPropertyDescriptors { (p: object) => object }
Object.getOwnPropertyDescriptors(o)
// { arr: { value: [1, 2, 3], writable: true, enumerable: true, configurable: true } }

// setPrototypeOf { (p1: object, p2: object) => object }
Object.setPrototypeOf({name: 'y'}, o) // {name: 'y'}，原型 === o

// keys { (p: object) => Array<string> }
Object.keys(o) // ['arr']

// values { (p: object) => Array<any> }
Object.values(o) // [[1, 2, 3]]

// entries { (p: object) => Array<Array<string|any>> }
Object.entries(o) // [['arr', [1, 2, 3]]]

// hasOwnProperty { (key: string) => boolean }
o.hasOwnProperty('arr') // true

// isPrototypeOf { (p: object) => boolean }
const p = {};
Object.setPrototypeOf(o, p);
p.isPrototypeOf(o) // true

// propertyIsEnumerable { (p: string) => boolean }
o.propertyIsEnumerable('arr') // true

// toLocaleString { () => string }
o.toLocaleString() // [object Object]

// toString { () => string }
o.toString() // [object Object]

// valueOf { () => object }
o.valueOf() // self
```

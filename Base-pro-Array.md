# Array

**Array API**

- Array.from // 将两类对象`array-like(object)|iterable(Set&Map)`转为真正的数组
- Array.isArray // 判断参数是否为数组类型
- Array.of // 将参数转成数组，弥补`Array()与new Array()`方法的不足

```ts
// Array.from { (arr, handler: (item: any) => any) => Array<any> }
const arr: Array<number|undefined> = [1, , 2, , 3];
const res: Array<number> = Array.from(arr, (item: number|undefined) => {
  return item || 0;
});
arr // [1, undefined, 2, undefined, 3]
res // [1, 0, 2, 0, 3]

// Array.isArray { (arr: Array<any>) => boolean }
const arr: Array<number> = [1, 2, 3];
const res: boolean = Array.isArray(arr);
res // true

// Array.of { (arg: any) => Array<any> }
const arr = new Array.of(1);
arr // [1]
```

**实例 API ES5**

- concat // 拼接数组
- every // 遍历数组，判断所有元素是否满足同一条件，返回`true继续|false退出`循环
- filter // 过滤器，返回满足条件元素所组成的数组
- forEach // 遍历数组
- indexOf // 正向获取匹配元素下标
- join // 数组转字符串，参数作为连接符
- lastIndexOf // 反向获取匹配元素下标
- map // 遍历数组，将返回的元素用空数组进行接收
- [x] pop // 删，移除数组最末项
- [x] push // 增，往数组最末追加元素
- reduce // 正向累加器
- reduceRight // 反向累加器
- [x] reverse // 反转数组
- [x] shift // 删，移除首项元素
- slice // 截取数组，选中区间`[)`
- [x] splice // 切割数组或替换数组元素，选中区间`[]`
- [x] sort // 升序或降序
- some // 遍历数组，判断是否有元素满足条件，返回`true`可退出循环
- toString // 数组转字符串，逗号作为连接符
- [x] unshift // 增，往数组首项位置追加元素
- valueOf // 自身

---

**实例 API ES6**

- [x] copyWithin // 将指定区间`[)`的元素替换到其他位置上
- find // 找出第一个符合条件的数组元素，全部不符合条件则返回 undefined
- findIndex // 找出第一个符合条件的数组元素对应的下标，全部不符合条件则返回 -1
- [x] fill // 将指定区间`[)`的元素全部抹去，用同个元素进行空位填充
- flat // 默认将二维数组拉平成一维数组，默认值为 1
- flatMap // 对每个成员都执行一个函数，然后对返回值执行 flat 方法
- includes // 判断数组中是否包含匹配元素

---

**举个栗子**

```ts
const arr: Array<number> = [1, 2, 3];

// concat { (Array<any>) => Array<any> }
arr.concat([4, 5]) // [1, 2, 3, 4, 5]

// every { (handler: (v: any) => boolean) => boolean }
arr.every((v: number) => {
  return v > 0
}) // true

// filter { (handler: (v: any) => Array<any>) => Array<any> }
arr.filter((v: number) => {
  return v > 1
}) // [2, 3]

// forEach { (handler: (v: any, i: number) => void) => void }
arr.forEach((v: number, i: number) => {
  // v i
})

// indexOf { (target: any) => number }
arr.indexOf((2)) // 1

// join { (symbol: string) => string }
arr.join('-') // 1-2-3

// lastIndexOf { (target: any) => number }
arr.lastIndexOf(2) // 1

// map { (handler: (v: any, i: number) => any) => Array<any> }
arr.map((v: number, i: number) => {
  // v i
  return v;
}) // [1, 2, 3]

// pop { () => Array<any> }
arr.pop() // [1, 2]

// push { (v: any) => Array<any> }
arr.push(4) // [1, 2, 3, 4]

// reduce { (handler: (a: number, b: number) => number) => number }
arr.reduce((a: number, b: number) => a + b) // 6

// reduceRight { (handler: (a: number, b: number) => number) => number }
arr.reduceRight((a: number, b: number) => a + b) // 6

// reverse { () => Array<any> }
arr.reverse() // [3, 2, 1]

// shift { () => Array<any> }
arr.shift() // [2, 3]

// slice { (start: number, end: number) => Array<any> }
arr.slice(1, 2) // [2]

// splice { (start: number, end: number, content?: any) => Array<any> }
// 两个参数
arr.splice(1, 2) // [2, 3]
arr // [1]
// 三个参数
arr.splice(1, 2, 5) // [2, 3]
arr // [1, 5]

// sort { (handler: (a: any, b: any) => a - b) => Array<any> }
arr.sort((a, b) => b - a) // [3, 2, 1]

// some { (v: any) => boolean }
arr.some((v: number) => v > 2) // true

// toString { () => string }
arr.toString() // 1,2,3

// unshift { (v: any) => Array<any> }
arr.unshift(0) // [0, 1, 2, 3]

// valueOf { () => Array<any> }
arr.valueOf() // self

// copyWithin { (i: number, start: number, end: number) => Array<any> }
arr.copyWithin(0, 1, 2) // [2, 2, 3]

// find { (handler: (v: any) => boolean) => any }
arr.find((v: number) => v > 1) // 2

// findIndex { (handler: (v: any) => boolean) => number }
arr.findIndex((v: number) => v > 1) // 1

// fill { (content: any, start: number, end: number) => Array<any> }
arr.fill(5, 1, 2) // [1, 5, 3]

// flat { (zIndex: number = 1) => Array<any> }
const _arr: Array<any> = [1, [2, 3]];
_arr.flat(1) // [1, 2, 3]

// flatMap { (handler: (v: any, index?: number, arr?: self) => Array<any>) => Array<any> }
const _arr: Array<any> = [1, [2, 3]];
_arr.flatMap((v: number) => [v, v * 2]) // [1, 2, 2, 4, 3, 6]
// 可传三个参数，分别为当前数组成员、起始位置下标、原数组

// includes { (target: any) => boolean }
arr.includes(1) // true
```

---

**数组排序**

```ts
const arr: Array<number> = [3, 4, 1, 5, 2];

// 通过API
arr.sort((a, b) => a - b);
arr // [1, 2, 3, 4, 5]

// 冒泡排序
function bubbleSort(arr: Array<string|number>) {
  for (let i = 0, l = arr.length; i < l; i++) {
    // arr[i] 对源数组每个元素进行比较
    for (let j = i + 1; j < l; j++) {
      // console.log('count');
      if (arr[i] > arr[j]) {
        // 从小到大排序
        const tmp = arr[i];
        arr[i] = arr[j]; // 换位
        arr[j] = tmp;
      }
    }
  }
}
bubbleSort(arr);
arr // [1, 2, 3, 4, 5]
```

---

**数字+字母+汉字排序**

```ts
const arr: Array<any> = [9,8,7,6,5,1,'在', '我', '里', '阿','z','a','h','m'];
arr.sort((a, b) => a.toString().localeCompare(b));
arr // [1, 5, 6, 7, 8, 9, "阿", "里", "我", "在", "a", "h", "m", "z"]
```

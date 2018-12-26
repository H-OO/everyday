# String

**String API**

- String.fromCharCode // 识别小于`0xFFFF`的字符
- String.fromCodePoint // 识别大于`0xFFFF`的字符

---

**实例 API ES5**

- charAt // 根据下标返回字符
- charCodeAt // 根据下标返回对应字符的`Unicode`值
- concat // 拼接字符串
- indexOf // 正向获取匹配字符串起始下标
- lastIndexOf // 反向获取匹配字符串的起始下标
- localeCompare // 获取引用字符串与参数字符串的排列顺序 (前-1、后1、同位置0)
- match // 正则匹配，返回一个数组，包含匹配字符、下标、源字符串
- replace // 替换
- search // 正则匹配，返回下标
- slice // 截取字符串，选中区间`[)`
- split // 字符串转数组，根据同一连接符进行分割
- substr // 选取字符串，参数 1 为起始下标，参数 2 为字符个数
- substring // 截取字符串，选中区间`[)`
- toLocaleLowerCase // 字母字符串转小写
- toLocaleUpperCase // 字母字符串转大写
- toLowerCase // 字母字符串转小写
- toUpperCase // 字母字符串转大写
- toString // self
- trim // 去首位空格
- valueOf // self

---

**实例 API ES6**

- startsWith // 源字符串是否以参数字符串开头
- endsWith // 源字符串是否以参数字符串结尾
- includes // 源字符串是否存在参数字符串
- padStart // 字符串头部长度补全
- padEnd // 字符串尾部长度补全
- repeat // 将源字符串复制 n 次

---

**举个栗子**

```ts
const str: string = 'abc';

// charAt { (index: number) => string }
str.charAt(1) // b

// charCodeAt { (index: number) => number }
str.charCodeAt(1) // 98，'b'对应的`Unicode`值

// concat { (str: string) => string }
str.concat('d') // abcd

// indexOf { (str: string) => number }
str.indexOf('c') // 2
str.indexOf('f') // -1

// lastIndexOf { (str: string) => number }
str.lastIndexOf('c') // 2
str.lastIndexOf('f') // -1

// localeCompare { (str: string) => number }
const num1: number = 1;
const num9: number = 9;
num1.toString().localeCompare(num9 as any) // -1
num9.toString().localeCompare(num1 as any) // 1
'a'.localeCompare('z') // -1
'b'.localeCompare('b') // 0
'啊'.localeCompare('在') // -1
const arr: Array<any> = ['在', '我', 9, 1, 'z', 'a', '0'];
arr.sort((a, b) => a.toString().localeCompare(b)) // ['0', 1, 9, '我', '在', 'a', 'z']

// match { (flag: RegExp) => Array<string> }
str.match(/a/) // ['a', index: 0, input: 'abc', groups: undefined]

// replace { (flag: string|RegExp, swap: string) => string }
str.replace(/a/, 'e') // ebc
str.replace(/(a)(b)(c)/, '$1-$2-$3') // a-b-c (正则块与 $ 符号的使用)

// search { (flag: string|RegExp) => number }
str.search('b') // 1

// slice { (start: number, end: number) => string }
str.slice(0, 1) // a

// split { (flag: string|RegExp) => Array<string> }
str.split(/b/) // ['a', 'c']

// substr { (index: number, length: number) => string }
str.substr(0, 2) // ab
str.substr(1, 2) // bc

// substring { (start: number, end: number) => string }
str.substring(0, 2) // ab
str.substring(1, 2) // b

// toLocaleLowerCase { () => string }
str.toLocaleLowerCase() // abc，'Abc' → 'abc'

// toLocaleUpperCase { () => string }
str.toLocaleUpperCase() // ABC

// toLowerCase { () => string }
str.toLocaleLowerCase() // abc，'Abc' → 'abc'

// toUpperCase { () => string }
str.toLocaleUpperCase() // ABC

// toString { () => string }
str.toString() // abc

// trim { () => string }
str.trim() // abc, ' abc ' → 'abc'

// valueOf { () => string }
str.valueOf() // abc

// startsWith { (flag: string) => boolean }
str.startsWith('a') // true

// endsWith { (flag: string) => boolean }
str.endsWith('c') // true

// includes { (flag: string) => boolean }
str.includes('b') // true 

// padStart
str.padStart(10, '-') // -------abc

// padEnd { (length: number, filler: string) => string }
str.padEnd(10, '-') // abc-------

// repeat { (count: number) => string }
str.repeat(3) // abcabcabc
```

---

**hot**

```
Q: slice、substr、substring的区别
A:
相同点：传入一个参数时，将参数作为起始下标进行正向选取
不同点1：传入一个负值参数时，`slice与substr`是以计算公式`起始下标=字符串长度+负值参数`，进行正向向选取；`substring`则返回源字符串
不同点2：传入两个参数时，`slice与substring`是以区间范围`[)`进行选取；`substr`则以参数1作为起始下标、参数2作为选取长度进行选取
```

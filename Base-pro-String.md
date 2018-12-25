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
- match // 正则匹配，返回一个数组，包含匹配字符、下标、源字符串
- replace // 替换
- search // 正则匹配，返回下标
- slice // 截取字符串，选中区间`[)`
- split // 字符串转数组，根据同一连接符进行分割
- substr // 选取字符串，参数 1 为起始下标，参数 2 为字符个数
- substring // 
- toLocaleLowerCase // 字母字符串转小写
- toLocaleUpperCase // 字母字符串转大写
- toLowerCase // 字母字符串转小写
- toUpperCase // 字母字符串转大写
- toString // self
- trim // 去首位空格
- valueOf // self

---

**实例 API ES6**

- endsWith // 源字符串是否以参数字符串结尾
- includes // 源字符串是否存在参数字符串
- padEnd // 字符串尾部长度补全
- padStart // 字符串头部长度补全
- repeat // 将源字符串复制 n 次
- startsWith // 源字符串是否以参数字符串开头

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

// match { (flag: RegExp) =>  }
str.match(/a/)

// replace
// search
// slice
// split
// substr
// substring
// toLocaleLowerCase
// toLocaleUpperCase
// toLowerCase
// toUpperCase
// toString
// trim
// valueOf
// endsWith
// includes
// padEnd
// padStart
// repeat
// startsWith

```

# RegExp

**元字符**

- \d // 数字
- \D // 非数字
- \s // 空格
- \S // 非空格
- \w // 字母数字下划线
- \W // 非字母数字下划线

---

**量词**

- \* // {0,} 可有可无
- \+ // {1,} 至少一次
- ? // {0,1} 可无或仅一次
- {n,m} // `n<=出现次数<=m`

---

**符号**

- . // 除换行符以外的其他单个字符
- ^ // 开始
- $ // 结束

---

**表达式**

- [] // 范围写法
- | // 任意一个
- () // 分组符
- [^] // 取反

---

**修饰符**

- g // 全局
- i // 不分大小写
- m // 多行
- u // 处理大于`\uFFFF`的`Unicode`字符
- y // 需从字符串的首位进行匹配
- s // 使`.`可以匹配任意单个字符

---

**实例 API**

- exec // 获取与正则匹配的字符串
- test // 判断是否存在与正则匹配的字符串

```ts
// exec { (p: string) => Array<string> }
/a/.exec('abc') // ['a', index: 0, input: 'abc', groups: undefined]

// test { (p: string) => boolean }
/a/.test('abc') // true
```

---

**动态内容选取**

场景：已知数据的包裹结构，需要将包裹的动态内容提取出来

通过`match`方法，排除无关字符串

```ts
// transform
const str = 'matrix(1, 0, 0, 1, -100, 0)';
const res = str.match(/[^a-z\(\)\s\,]+/g).slice(4);
console.log(res); // ['-100', '0']

// 参数序列化
const str = 'http://xxx.com/a/b.html?username=1&password=123';
const res = str.match(/\?.*/)[0].slice(1).split('&');
const obj: any = {};
res.forEach((v) => {
  const tmp = v.split('=');
  const key = tmp[0];
  const value = tmp[1];
  obj[key] = value;
});
```

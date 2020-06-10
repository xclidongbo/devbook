# 数据类型

## `typeof`操作符
`typeof XXX`
- undefined
- boolean
- string
- number
- object
- function
- symbol


## undefined类型

## Null类型
Null类型只有一个特殊值: null.
null是一个空对象指针.`typeof null` 返回的是是 `object`.
```js
let car = null;
console.log(typeof car);  // "object”
```
undefined是null的子类.
所以以下等式成立
```js
console.log(null == undefined);  // true
```

## Boolean类型
|数据类型|为true|为false|
|-|-|-|
|Boolean|true|false|
|String|非空字符串|""(空字符串)|
|Number|非0数字|0,NaN|
|Object|任意对象|null|
|Undefined|n/a|undefined|


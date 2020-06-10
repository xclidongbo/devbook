## 函数类型

---

### 函数声明

```
// 函数声明
function sum(x, y) {
  return x+y;
}

// 函数表达式

let mySum = function (x,y) {
  return x+y;
};
```


```
function sum(x: number, y: number): number {
  return x+y;
}
```

### 函数表达式

```
let mySum = function (x: number, y: number): number {
  return x + y;
}

//等价于
let mySum: (x: number, y: number) => number = function (x: number, y: number):number {
  return x+ y;
}

```
### 用接口定义函数的形状

```
interface SearchFunc {
  (source: string, subString: string): boolean;
}
let mySearch: SearchFunc;
mySearch = function(source: string, subString: string) {
  return source.search(subString) !== -1;
}
```

### 可选参数

```
function buildName(firstName: string, lastName?: string) {
  if (){
    return firstName + ' ' + lastName;
  }
  else{
    return firstName;
  }
}
let tomcat = buildName('Tom', 'Cat');
let tom = buildName('Tom')
```
> 可选参数后面不允许再出现必需参数.


### 参数默认值

```
function buildName(firstName: string, lastName: string = 'Cat') {
  return firstName + ' ' + lastName;
}

let tomcat = buildName('Tom', 'Cat');
let tomcat = buildName('Tom');

```

### 剩余参数
```
function push(array, ...items) {
  items.forEach(function(item) {
    array.push(item);
  })
}
let a: any[] = [];---
push(a,1,2,3)
```


### 重载

重载允许一个函数接受不同数量或类型的参数,作出不同处理.

利用联合类型, 我们可以这么实现:

```
function reverse(x: string|number): number|string {
  if (typeof x === 'number') {
    return Number(x.toString().split('').reverse().join(''));
  }else if (typeof x === 'string') {
    return x.split('').reverse().join('');
  }
}

```
我们也可以使用重载定义多个`reverse`的函数类型

```
function reverse(x: number): number;
function reverse(x: string): string;
function reverse(x: number | string): number | string {
    if (typeof x === 'number') {
        return Number(x.toString().split('').reverse().join(''));
    } else if (typeof x === 'string') {
        return x.split('').reverse().join('');
    }
}
```





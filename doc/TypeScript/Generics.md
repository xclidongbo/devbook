
## 泛型


----


### DEMO

以下缺陷: 没有定义返回值的类型:
```
function createArray(length: number, value: any): Array<any> {
  let result = [];
  for (let i=0; i<length; i++) {
    result[i] = value;
  }
  return result;
}

createArray(3, 'x');

```

泛型Demo:

```
function crateArray<T>(length: number, value: T): Array<T> {
  let result: T[] = [];
  for (let i = 0; i< lenght; i++) {
    result[i] = value;
  }
  return result;
}
//手动指定
createArray<string>(3, 'x');

//也可以不用指定
createArray(3, 'x')
```

### 多个参数类型


```
function swap<T, U>(tuple: [T, U]): [U, T] {
    return [tuple[1], tuple[0]];
}

swap([7, 'seven']); // ['seven', 7]
```


### 泛型约束

```

function loggingIdentity<T>(arg: T): T {
    console.log(arg.length);
    return arg;
}
//T不包含length就会报错
```
改进

```
interface Lengthwise {
    length: number;
}

function loggingIdentity<T extends Lengthwise>(arg: T): T {
    console.log(arg.length);
    return arg;
}
```
多个参数,互相约束

```
function copyFields<T extends U, U>(target: T, source: U): T {
    for (let id in source) {
        target[id] = (<T>source)[id];
    }
    return target;
}

let x = { a: 1, b: 2, c: 3, d: 4 };

copyFields(x, { b: 10, d: 20 });
```

### 泛型接口

```
interface CreateArrayFunc {
    <T>(length: number, value: T): Array<T>;
}

let createArray: CreateArrayFunc;
createArray = function<T>(length: number, value: T): Array<T> {
    let result: T[] = [];
    for (let i = 0; i < length; i++) {
        result[i] = value;
    }
    return result;
}

createArray(3, 'x'); // ['x', 'x', 'x']
```


### 泛型类


```
class GenericNumber<T> {
    zeroValue: T;
    add: (x: T, y: T) => T;
}

let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function(x, y) { return x + y; };

```


### 泛型参数的默认类型

```
function createArray<T = string>(length: number, value: T): Array<T> {
  let result: T[] = [];
  for (let i = 0; i < length; i++) {
      result[i] = value;
  }
  return result;
}

```


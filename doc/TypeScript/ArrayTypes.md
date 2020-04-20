
## 数组的类型

---



### 类型+方括号

```
let fib: number[] = [1,2,3,4]
```

数组的项中不允许出现其它类型


### 数组泛型

我们也可以使用数组泛型来表示数组

```
let fib: Array<number> = [1,2,3,4];
```

### 用接口表示数组

```
interface NumberArray {
  [index: number]: number;
}
let fib: NumberArray = [1,2,3,4]

```

`NumberArray`表示: 只要索引的类型是数字时, 那么值的类型必须是数字

### 类数组

类数组不是数组类型
```
function sum() {
  let args: number[] = arguments;
}

//以上会报错

function sum() {
  let args: {
    [index: number]: number;
    length: number;
    callee: Function;
  } = arguments;
}
```
### any在数组中的应用

```
let list: any[] = ['liu', 25, {website: 'http://www.baidu.com'}]
```


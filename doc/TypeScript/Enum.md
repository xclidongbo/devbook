## 枚举


----



### DEMO

```
enum Days {Sun, Mon, Tue, Sat};
```


枚举成员会从0开始递增的数字,同时也会对枚举值到枚举名反向映射.

```
enum Days {Sun, Mon, Tue, Wed, Thu, Fri, Sat};

console.log(Days["Sun"] === 0); // true
console.log(Days["Mon"] === 1); // true
console.log(Days["Tue"] === 2); // true
console.log(Days["Sat"] === 6); // true

console.log(Days[0] === "Sun"); // true
console.log(Days[1] === "Mon"); // true
console.log(Days[2] === "Tue"); // true
console.log(Days[6] === "Sat"); // true
```


### 手动赋值

```
enum Days {Sun = 3, Mon = 1, Tue, Wed, Thu, Fri, Sat};
console.log(Days["Sun"] === 3); // true
console.log(Days["Wed"] === 3); // true
console.log(Days[3] === "Sun"); // false
console.log(Days[3] === "Wed"); // true
```

### 常数项和计算所得项


```
enum Color {Red, Green, Blue = "blue".length};
```
### 常数枚举

```
const enum Directions {
  Up,
  Down,
  Left,
  Right
}

let directions = [Directions.Up, Directions.Down, Directions.Left, Directions.Right];

// 编译结果
var directions = [0 /* Up */, 1 /* Down */, 2 /* Left */, 3 /* Right */];

```

> 常数枚举与普通枚举的区别是, 它会在编译期被删除, 并且不能包含计算成员.

### 外部枚举

```
declare enum Directions {
  Up,
  Down,
  Left,
  Right
}

let directions = [Directions.Up, Directions.Down, Directions.Left, Directions.Right];

// 编译结果
var directions = [Directions.Up, Directions.Down, Directions.Left, Directions.Right];

```
> 外部枚举 declare定义的类型只会用于编译期的检查,编译结果中会被删除.


同时使用`declare`和`const`:

```
declare const enum Directions {
    Up,
    Down,
    Left,
    Right
}

let directions = [Directions.Up, Directions.Down, Directions.Left, Directions.Right];

// 编译结果

var directions = [0 /* Up */, 1 /* Down */, 2 /* Left */, 3 /* Right */];
```



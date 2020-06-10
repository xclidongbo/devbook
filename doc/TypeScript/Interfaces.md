## 接口
---

### 概念
接口是对行为的抽象,具体如何行动需要由类去实现.

```
interface Person {
  name: string;
  age: number;
}
let tom: Person = {
  name: 'Tom',
  age: 25
}
```
定义的变量比接口少一些或者多一些属性是不被允许的:

```
interface Person {
  name: string;
  age: number;
}
let tom: Person = {
  name: 'Tom'
}

```
### 可选属性

有时我们希望不要完全匹配一个形状,那么可以用可选属性:

```
interface Person {
  name: string;
  age?: number;
}
let tom: Person = {
  name: 'Tom'
}

```
> 可选属性的含义是该属性可以不存在
> 但这时候依然不允许添加未定义的属性.

### 任意属性

我们希望一个接口允许有任意的属性
```
interface Person {
  name: string;
  age?: number;
  [propName: string]: any;
}
let tom: Person = {
  name: 'Tom',
  gender: 'male'
}
```

> 一旦定义了任意属性,那么确定属性和可选属性必须是任意属性的子集.

```
let tom: Person = {
  name: 'Tom';
  age: 25;
  gender: 'male'
}
// 报错, 任意属性的值允许是string,但可选属性age却是number,number不是string的子集,所以报错.

```

一个接口只能定义一个任意属性,如果接口中有多个类型的属性,则可以在任意属性中使用联合类型.

```
interface Person {
    name: string;
    age?: number;
    [propName: string]: string | number;
}

let tom: Person = {
    name: 'Tom',
    age: 25,
    gender: 'male'
};

```

### 只读属性

有时候我们希望对象中的一些字段只在创建的时候被赋值,那么可以用`readonly`定义只读属性

```
interface Person {
  readonly id: number;
  name: string;
  age?: number;
  [propName: string]: any;
}
```

> 只读的约束存在于第一次给对象赋值的时候,而不是第一次给只读属性赋值的时候.






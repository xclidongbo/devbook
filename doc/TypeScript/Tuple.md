## 元组

----


数组合并了相同类型的对象,而元组合并了不同类型的对象.

### DEMO

定义一对值分别为 `string`和`number`的元组:

```
let tom: [string, number] = ['Tom', 25];


let tom: [string, number];
tom[0] = 'Tom';
tom[1] = 25;


let tom: [string, number];
tom = ['Tom', 25];

let tom: [string , number];
tom = ['Tom']; //报错

```

### 越界的元素

```
let tom: [string, number];
tom = ['Tom', 25];
tom.push(true); // 报错

```

>添加越界的元素时, 它的类型会被限制为元组中每个类型的联合类型.






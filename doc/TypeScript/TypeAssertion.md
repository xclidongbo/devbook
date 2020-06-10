## 类型断言

----


### 语法

```
值 as 类型

```
或者

```
<类型>值
```

### 类型断言的用途

#### 将一个联合类型断言为其中一个类型

```
interface Cat {
  name: string;
  run(): void;
}
interface Fish {
  name: string;
  swim(): void;
}

function getName(animal: Cat | Fish) {
  return animal.name;
}

```

而有时候我们确实需要在还不确定类型的时候就要访问其中一个类型特有的属性和方法

```
interface Cat {
  name: string;
  run(): void;
}
interface Fish {
  name: string;
  swim(): void;
}
function isFish(animal: Cat | Fish) {
  if (typeof animal.swim === 'function') {
    return true;
  }
  return false;
}

```
> 以上例子就会报错,因为animal没有swim方法

如果用断言可以这样写
```
interface Cat {
  name: string;
  run(): void;
}
interface Fish {
  name: string;
  swim(): void;
}
function isFish(animal: Cat | Fish) {
  if (typeof (animal as Fish).swim === 'function') {
    return true;
  }
  return false;
}

```

> 断言只能欺骗TypeScript编译器,如果滥用,也会导致运行时错误.


#### 将一个父类断言为更加具体的类

```
class ApiError extends Error {
  code: number = 0;
}
class HttpError extends Error {
  statusCode: number = 200;
}

function isApiError(error: Error) {
  if (error instanceof ApiError) {
    return true;
  }
  return false;
}

```

如果是一个JavaScriprt的类,能够用instanceof来判断.
如果是一个TS的接口,interface,这时候无法用instanceof来判断了.
此场景只能用断言来判断.

```
interface ApiError extends Error {
  code: number;
}
interface HtppError extends Error {
  statusCode: number;
}

function isApiError(error: Error) {
  if (typeof (error as ApiError).code === 'number') {
    return true;
  }
  return false;
}


```


#### 将任何一个类型断言为 any

```
(window as any).foo = 1
```

#### 将any断言一个具体的类型

```
function getCacheData(key: string): any {
    return (window as any).cache[key];
}

interface Cat {
    name: string;
    run(): void;
}

const tom = getCacheData('tom') as Cat;
tom.run();

```


### 类型断言的限制

- 联合类型可以被断言为其中一个类型
- 父类可以被断言为子类
- 任何类型都可以被断言为any
- any可以被断言为任何类型


### 双重断言

### 类型断言和类型转换

### 类型断言vs类型声明

### 类型断言vs泛型

```
function getCacheData<T>(key: string): T {
  return (window as any).cache[key];
}
interface Cat {
  name: string;
  run(): void;
}
const tom = getCacheData<Cat>('tom');
tom.run()

```

# 声明
```js
let sum = a + b //没有分号, 不推荐
let diff = a - b; //推荐

// 有效,但容易出错,不推荐
if (test)
 console.log(test);

//推荐
if (test) { console.log(test);}

```

# 变量

```js
var message = 'hi';
```
## var 声明范围
### 局部变量
```js
function test() {
 var message = "hi"; // local variable
}
test();
console.log(message);//错误
```
### 全局变量
```js
function test() {
 message = "hi"; // global variable
}
test();
console.log(message); // "hi”
```
### var声明提升
```js
//可以重复声明不报错
function foo() {
 var age = 16;
 var age = 26;
 var age = 36; 
 console.log(age);
}
foo(); // 36
```

## let声明
只在作用域内有用.不能重复声明

### 临时死区

### 全局声明
```js
var name = 'Matt';
console.log(window.name); // 'Matt'

let age = 26;
console.log(window.age);  // undefined
```

### 在循环中的let声明
```js
for (let i = 0; i < 5; ++i) {
 // do loop things
}
console.log(i); // ReferenceError: i is not defined
```

## const声明
const声明后,值不能重新定义.
const声明仅仅强制指向它的指针指向.如果一个const变量指向一个对象,改变对象的属性并不违反原则.
```js
const person = {};
person.name = 'Matt'; // ok
```

## 声明的样式和最好的练习
- 不要使用var
- 偏爱const多于let




### 泛型的基本用法


#### 泛型类

```
class MyClass<T> {
  fun method(param: T): T {
    return param
  }
}

//使用
val myClass = MyClass<Int>()
val result = myClass.method(123)

```

#### 泛型方法

```
class MyClass {
  fun <T> method(param: T):T {
    return param
  }
}

val myClass = MyClass()
myClass.method<Int>(123)
myClass.method(123)

// 对泛型的类型限制

 fun <T: Number> method(param: T):T {
   return param
 }
```














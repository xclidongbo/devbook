
### 类委托和委托属性

#### 类委托

关键字是`by`, 我们只需要在接口声明的后面使用by关键字,再接上受委托的辅助对象. 就可以免去很多方法.

```
class MySet<T>(val helperSet:HashSet<T>): Set<T> by helperSet {
  fun helloWorld = println("Hello World")
  orverride fun isEmpty() = false
}
```


> 核心思想: 此类的实现交给另外一个类去完成,而委托属性的核心思想是将一个属性的具体实现委托给另一个类去做.


#### 委托属性
```
class MyClass {
  var p by Delegate()
}

class Delegate {
  var propValue:Any? = null
  operator fun getValue(myClass:MyClass, prop: KProperty<*>):Any? {
    return propValue
  }
  operator fun setValue(myClass:MyClass, prop: KProperty<*>, value: Any?) {
    propValue = value
  }
}

```


## 定义静态方法

### 单例类(非静态方法)
```
object Util {
  fun doAction(){
    println("do action")
  }
}
```


### 类中的某一个方法变成静态方法的调用方式(非静态方法)

实际上调用类中伴生对象的doAction2方法.
```
class Util {
  fun doAction1 () {

  }

  companion object {
    fun doAction2 () {

    }
  }
}

```


### 静态方法

#### 注释
@JvmStatic 注释, 只能夹在单例类或者companion object的方法上
```
class Util {
  fun doAction1 () {

  }

  companion object {
    @JvmStatic
    fun doAction2 () {

    }
  }
}

```

#### 顶层方法

例如.kt文件中,只有方法.
kotlin方法会把所有的顶层方法编译成静态方法



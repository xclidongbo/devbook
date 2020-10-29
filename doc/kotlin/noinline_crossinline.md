
### noinline和crossinline

inline会自动的给所有参数全部进行内联.如果我们只想内联一个参数,就用到了`noinline`.

```
inline fun inlineTest(block1:()->Unit, noinline block2:()->Unit){}
```

> 内联的函数类型参数,在编译的时候进行代码替换,因此它没有真正的参数属性.非内联的函数类型参数可以自由的传递给其它函数,因为它就是一个真实的参数.而内联的函数类型参数,只允许传递给另外一个内联函数,这也是它最大的局限性.
> 另外,内联函数和非内联函数还有个重要区别,那就是内联函数所引用的Lambda表达式中可以使用return关键字来进行函数返回,而非内联函数只能进行局部返回.

```
fun printString(str: String, block:(String)->Unit) {
  println("printString begin")
  block(str)
  println("printString end")
}
fun main(){
  println("main start")
  val str = ""
  printString(str) {s->
    println("lambda start")
    if (s.isEmpty()) return@pringString
    println(s)
    println("lambda end")
  }
  println("main end")
}
```

执行结果:

```
main start
printString begin
lambda start
printString end
main end
```

如果printString函数加了inline
```
inline fun printString(str: String, block:(String)->Unit) {
  println("printString begin")
  block(str)
  println("printString end")
}
fun main(){
  println("main start")
  val str = ""
  printString(str) {s->
    println("lambda start")
    if (s.isEmpty()) return
    println(s)
    println("lambda end")
  }
  println("main end")
}


```

执行结果:

```
main start
printString begin
lambda start

```

> 将高阶函数声明成内联函数是好的编程习惯

如果我们再高阶函数中创建了另外的Lambda或者匿名类的实现,并且在这些视线中调用函数类型参数,此时再将高阶函数声明成内联函数,就一定会提示错误.

```
// 会出现错误,原因是高阶函数的匿名类实现中不允许出现return关键字,内联函数的Lambda表达式中允许出现return关键字,造成了冲突.
inline fun runRunable(block: ()->Unit){
  val runnable = Runnable {
    block()
  }
  runnable.run()
}
```

正确写法:

```
inline fun runRunable(crossinline block: ()->Unit){
  val runnable = Runnable {
    block()
  }
  runnable.run()
}

```

### 内联函数

demo:

```
fun num1AndNum2(num1:Int,num2:Int,opersion:(Int,Int)->Int):Int{
  val result = opersion(num1,num2)
  return result
}
```
以上代码每次调用,都会创建匿名函数,会造成额外的内存开销.

为了解决这个问题引入了内联函数,Kotlin会将内联函数中的代码再编译的时候自动替换到其它地方,节省带来的运行时开销.

```

inline fun num1AndNum2(num1:Int,num2:Int,opersion:(Int,Int)->Int):Int{
  val result = opersion(num1,num2)
  return result
}

```


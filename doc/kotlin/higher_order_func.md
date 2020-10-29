
### 定义高阶函数

```
//定义

fun num1AndNum2(num1:Int,num2:Int,operation:(Int,Int)->Int):Int {
  val result = operation(num1,num2)
  return result
}

fun plus(num1: Int, num2:Int):Int {
  return num1 + num2
}

fun minus(num1:Int, num2:Int): Int {
  return num1 - num2
}

// 调用
val result1 = num1AndNum2(num1,num2, ::plus)
val result2 = num1AndNum2(num1,num2, ::minus)
```

如果使用Lambda表达式的写法就是:

```

val result1 = num1AndNum2(num1,num2){ n1,n2->
  n1+n2
}
val result2 = num1AndNum2(num1,num2){ n1,n2->
  n1-n2
}

```


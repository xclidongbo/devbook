
### 字符串内嵌表达式


```
val brand = "SameSung"
val price = 1222
println("Cellphone(brand=$brand,price=$price)")

```

### 函数的参数默认值


```

fun printParams(num:Int, str: String = "hello"){
  println("num is $num, str is $str")
}

printParams(123);
```

如果第一个参数有默认值,可以这样写:

```
fun printParams(num:Int = 100, str: String){
  println("num is $num, str is $str")
}

printParams(str = "world)
```


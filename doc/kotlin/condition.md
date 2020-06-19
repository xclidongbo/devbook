
## 程序的逻辑控制


### if条件语句


### when条件语句

when语句允许传入一个任意类型的参数,然后可以再when的结构体中定义一系列的条件
```
匹配值 -> {执行逻辑}

```

```
fun checkNumber(num: Number) {
  when (num) {
    is Int -> println('number is Int')
    is Double -> println('number is double')
    else -> println('number not support')
  }
}

```

when不带参数的用法:

```
fun getScore(name: String) = when {
  name.startWith("Tom") -> 86
  name == "jim" -> 88
  else -> 0
}
```


### 循环语句

// 打印0-10
```
for (i in 0..10) {

}
```

// 打印 0,2,4,6,8
```
for(i in 0 until 10 step 2) {
  println(i)
}
```


// 打印 10-1
```
for (i in 10 downTo 1) {
  println(i)
}

```




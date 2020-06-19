
## 标准函数


### let

### with

with 接收两个参数
```
val result = with(obj){
  "value" //with 函数的返回值
}
```

作用: 可以连续调用同一个对象的多个方法时让代码更加精简.

原始代码

```
  val list = listOf("Apple", "Banana","Orange")
  val builder = StringBuilder()
  builder.append("Start eating fruits.\n")
  for (fruit in list) {
      builder.append(fruit).append("\n")
  }
  builder.append("Ate all fruits")
  val result = builder.toString()
  println(result)

```

精简后:

```
val list = listOf("Apple", "Banana","Orange")
val result = with(StringBuilder()) {
    append("Start eating fruits.\n")
    for (fruit in list){
        append(fruit).append("\n")
    }
    append("Ate all fruit")
    toString()
}
println(result)

```

### run

用法和场景和with相似:

val list = listOf("Apple", "Banana","Orange")
```
val result = StringBuilder().run {
    append("Start eating fruits.\n")
    for (fruit in list){
        append(fruit).append("\n")
    }
    append("Ate all fruit")
    toString()
}
println(result)

```

### apply

```
val result = obj.apply {
  //obj的上下文
}
// result == obj

```



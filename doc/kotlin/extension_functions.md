
## 扩展函数


格式:

```
fun ClassName.methodName(param1:Int, param2:Int): Int{
  return 0
}

```


```
fun String.lettersCount(): Int {
    var count = 0
    for (char in this) {
        count++
    }
    return count
}

// 使用

val count = "ABC1231231".lettersCount()

```
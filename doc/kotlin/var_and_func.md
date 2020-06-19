
## 变量和函数

### 变量

val
var

### 函数

```
// 两个入参, 返回最大值
fun largerNumber(num1: Int, num2: Int): Int {
  return max(num1, num2)
}

```

精简为

```

fun largeNumber(num1: Int, num2: Int) = if (num1>num2) num1 else num2
```



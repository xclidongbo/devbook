
## 运算符重载

两个对象相加,返回第三个对象

```
class Money(val value: Int) {
  operator fun plus(money:Money):Money {
    val sum = value + money.value
    return Money(sum)
  }
}

val money1 = Money(5)
val money2 = Money(10)
val money3 = money1 + money2
```


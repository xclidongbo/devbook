### 实现一个自己的lazy函数

```
class Later<T>(val block: ()->T) {
  var value: Any? = null
  operator fun getValues(any: Any?, prop: KProperty<*>):T {
    if(value == null) {
      value = block()
    }
    return values as T
  }
}

fun <T> later(block:()->T)=Later(block)

//使用
val uriMatcher by later {
  val matcher = UriMatcher(UriMatcher.NO_MATCH)
  matcher.addURI(authority,"book",bookDir)
  matcher
}
```





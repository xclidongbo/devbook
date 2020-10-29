
### 简化ContentValues


demo:

```
val values = ContentValues()
values.put("name", "Game of Thrones")
values.put("page", 720)
db.insert("Book", null, values)

```


简化后

```
fun cvOf(vararg pairs: Pair<String, Any?>)= ContentValues().apply {
  for(pair in pairs){
    val key = pair.first
    val value = pair.second
    when(value) {
      is Int -> put(key, value)
      is Long -> put(key, value)
      is Short -> put(key, value)
      is Double -> put(key, value)
      null -> putNull(key)
    }
  }
}

```


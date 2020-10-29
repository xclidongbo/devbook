###简化 SharePreferences

demo
```
val editor = getSharePreferences("data", Context.MODE_PRIVATE).edit()
editor.putString("name","Tom")
editor.putInt("age",26)
editor.putBoolean("married",false)
editor.apply()

```


简化思想:
1. 扩展
2. 高阶函数

```
fun SharedPreferences.open(block: SharedPreferences.Editor.()->Unit) {
  val editor = edit()
  editor.block()
  editor.apply()
}
```

使用: 

```
getSharePreferences("data", Context.MODE_PRIVATE).open{
  putString("name", "Tom")
}

```






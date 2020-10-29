
### infix构建可读语法

String类中有一个startsWith函数,借助infix函数,我们可以用另外一种方法来表达这段代码
```
infix String.beginWith(prefix:String) = startsWith(prefix)

//用法
if ("Hello World" beginWith "Hello"){

}

```

其它demo:

```
infix fun <T> Collection<T>.has(element:T) = contains(element)

//用法

if (list has "Apple") {

}
```



### 密封类

demo:

```
interface Result
class Success(val msg: String) :Result
class Failture(val error:Exception): Result


//定义一个方法
fun getResultMsg(result: Result) = when(result){
  is Success -> result.msg
  is Failture -> result.error.message
  else -> throw IllegalArgumentException()
}

```

明明知道else永远不可能走,可为了准确编译,只能写else分支的代码,编写else条件还有一个潜在风险,如果我们新增了一个Unknown类实现了Result接口,但忘了在getResultMsg方法中写相应分支, 这会造成运行时执行该分支时候错误.

为了很好的解决这个问题,引入了密封类
关键字为:
```
sealed class
```

最后可优化为:
```
sealed class Result
class Success(val msg: String) : Result()
class Failture(val error:Exception): Result()


//只需要这样实现
fun getResultMsg(result: Result) = when(result){
  is Success -> result.msg
  is Failture -> result.error.message
}
```

> 这就是密封类的主要使用方法. 密封类及其子类只能顶一个同一个文件的顶层,不能嵌套在其它类中,这是被密封类的底层实现机制所限制的.


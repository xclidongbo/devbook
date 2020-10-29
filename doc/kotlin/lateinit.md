## 变量延迟初始化

```
class MainActivity: AppCompatActivity(), View.onClickListener {
  private var adapter: MsgAdapter? = null
  override fun onCreate(saveInstanceState: Bundle?){
    ***
    adapter = MsgAdapter(msgList)
    ***
  }
  override fun onClick(v: View?){
    adapter?.notifyItemInserted(msgList.size -1)
  }
}
```

> 注意`adapter`当你的代码中有了越来越多的全局实例变量时,这个问题会越来越明显,可能需要编写大量的判空处理才行,否则编译肯定无法通过.
> 解决办法就是对全局变量进行延迟初始化

```

class MainActivity: AppCompatActivity(), View.onClickListener {
  private lateinit var adapter: MsgAdapter
  override fun onCreate(saveInstanceState: Bundle?){
    ***
    adapter = MsgAdapter(msgList)
    ***
  }
  override fun onClick(v: View?){
    adapter.notifyItemInserted(msgList.size -1)
  }
}

```

> 风险: 如果没有初始化的情况下使用它,就会闪退. 所以当你对一个全局变量使用了`lateinit`关键字的时候, 一定要确认它进行了初始化.

判断是否进行了初始化

```
if (!::adapter.isInitialized){
  adapter = MsgAdapter(msgList)
}
```


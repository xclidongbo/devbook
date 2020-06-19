
## Activity的生命周期

### 返回栈

Android是用任务(task)来管理Activity的, 一个任务就是一组放在栈里的Activity的集合, 这个栈也叫做返回栈.

### Activity状态

每个Activity在生命周期中最多可能会有4种状态.

- 运行状态: 位于栈顶,
- 暂停状态: 不再处于栈顶位置,但依然可见.
- 停止状态: 不再处于栈顶位置,并且完全不可见.
- 销毁状态: 从栈顶移除后就变成了销毁状态.

### Activity的生存期

Activity类中定义了7个回调方法,覆盖了生命周期的每一个环节.
- onCreate(): 第一次被创建的时候调用, 完成初始化操作,比如加载布局,绑定事件等;
- onStart(): 不可见变为可见的时候调用;
- onResume(): 准备好和用户进行交互的时候调用.此时的Activity一定处于返回栈的栈顶,并且处于运行状态;
- onPause(): 这个方法在Activity准备去启动或者恢复另一个Activity的时候调用. 这个时候,通常将一些消耗CPU的资源释放掉,以及保存一些数据;
- onStop(): 这个方法会在Activity完全不可见的时候调用.它和onPause的区别在于,如果启动的是对话框的Activity,那么onPause就会被执行,而onStop方法并不会执行;
- onDestroy(): Activity被销毁之前调用;
- onRestart(): Activity由停止状态变成成运行状态,也就是被重新启动


除了onRestart,又可分为3种生存期

- 完整生存期
- 可见生存期
- 前台生存期


### Activity被回收的情况

onSaveInstanceState()方法调用

### Activity的启动模式

启动模式分4种

- standard
- singleTop
- singleTask
- singleInstance

### Activity的最佳实践

#### 知晓当前是在哪一个Activity

#### 随时随地退出程序

#### 启动Activity的最佳方法



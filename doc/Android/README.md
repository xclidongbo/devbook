
Android学习路线

----


### 语言

#### Java
[深入理解Java虚拟机](https://book.douban.com/subject/34907497/)
[深入理解Android Java虚拟机ART](https://book.douban.com/subject/33390277/)

#### Kotlin
#### Flutter


### Android Studio

- AS快捷键
- AS插件
- AS Profile

### Porject Structure
熟悉项目的目录结构,资源文件,Gradle文件


### Android基础支持

#### 四大组件

- Activity
- Service
- Broadcast Receiver
- Content Provider

#### Intents

- type of intent
- Intent filter

#### Static User Interface

- View--- Button,ImageView,TextView,EditText, and etc;
- ViewGroup - LinearLayout, RelativeLayout,FrameLayout: 三大传统布局
- ConstraintLayout: 约束布局


#### Dynamic User Interface

- RecyclerView --- 列表类的布局首选控件
- ViewPager
- Spinner

#### CustomView
以下知识点
- Canvas
- Bitmap
- Paint

#### UI Resources
使用资源文件会让代码的可修改性更高
- Drawables
- String
- Styles

#### Fragments
倡导 单 Activity + 多个 Fragment的组合
- Fragment Lifecycle
- Fragment Manager

#### Support User Interface
同样是一些功能组件,需要知道这是什么东西,基本的用法
- ProgressBar - 进度条
- Dialogs - 弹框
- Toast & Snackbar - 提示

#### Storage
持久化存储
- Shared Preferences - 适合存储字段
- File Systems - 文件存储
- Database - RoomDB - 数据库存储

#### Build
AS默认使用Gradle进行编译, Gradle的使用必须要熟悉, 以及如何区分开发版本和Release版本,渠道包技术,以及ASM等
- Gradle
- Debug/Release Configuration
- 多渠道打包
- ASM

#### Threading
Android App只有一个主线程,其余的我们称之为工作线程.
如何高效的创建和释放线程,线程池,线程间通信,Message-Looper-Handler模型这些知识点都要聊熟于心,Binder通信也要掌握的知识.
- Threads
- Handler/Looper/Message/MessageQueue
- AIDL/Binder

#### Debugging
Debug工具

- Memory profiling - MAT, AS Memory Profile
- Logging - Log包含非常丰富的信息
- Systrace - 工具可以查看一段时间内手机系统各个进程的运行状态
- Exceptions - 各种异常
- Error Handling - Error是必须要解决的问题

#### Memory Leak
内存泄漏的处理

#### 3rd Party Library

- Image Loading - Glide, Picasso
- Dependency Injection - Dagger
- Networking - Retrofit
- MultiThreading - RxJava, Coroutines

#### Data Format
常见的数据保存流格式
- JSON -GSON
- Flat Buffer
- Protocol Buffer

#### Android Jetpack
- Foundation Components — AppCompat, Android KTX, Multidex
- Architecture Components — LiveData, ViewModel, DataBinding, Paging, Work Manager, Navigation
- Behaviour Components - Download Manager, Media Playback, Notification, Permissions, Preference, Sharing, Slice
- UI Component - Animation & Transition, Android Auto, Emoji, Palette, Android TV, Android Wear


#### Architecture

- MVVM
- MVP


#### 单元测试

- Local Unit Testing
- Instrumentation Testing

#### Security
- 加密和解密

#### App Release
应用发布相关支持, 国内还得加上多渠道打包,插件化
- keystore file
- app bundle
- playstore
- 多渠道打包
- 插件化



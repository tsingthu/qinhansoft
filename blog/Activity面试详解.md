Activity面试详解.md
# 一.Activity生命周期
##   1.什么是Activity？
> 在应用中，Android与用户交互的接口，它提供了一个界面让用户进行点击、滑动等操作，这个接口就是Activity。
## 2.Activity的4种状态
> running：处于活动状态，用户可以进行操作。这时Activity处于栈顶。
> paused：Activity失去焦点，栈顶被非全屏或透明的Activity所占据。
> stoped：Activity被另一个Activity所完全覆盖的时候。此时Activity已不再可见，但是它的内存信息、成员变量等数据都可能还存在。
> killed：Activity已经被系统回收，它所保存的数据已经都不存在。
## 3.Activity生命周期分析
### Activity启动：onCreate()->onStart()->onResume()
> onCreate():Activity被创建的时候被调用，是Activity生命周期第一个被调用的方法。
> onStart():Activity正在启动，已经处于用户可见的状态，但是还没有前台显示，就是说，这个时候，Activity还不能响应用户的操作。
> onResume():Activity已经处于前台。
### 点击Home键回到主界面(Activity不可见）：onPause()->onStop()
> onPause():Activity处于pause状态。对应onResume()
> onStop():表明Activity已经被停止，或者已经被完全覆盖。
### 再次回到原Activity时：onRestart()->onStart()->onResume()
> onRestart():表示Activity正在被重新启动，这时Activity正在从不可见变为可见状态。
### 退出当前Activity时：onPause()->onStop()->onDestory()
> onDestory():整个生命周期中的最后一个方法，表明Activity正在被销毁。
## 4.Android进程优先级
前台、可见、服务、后台、空
# 二.Android任务栈
FILO，任务栈并不是唯一的。
# 三.Activity启动模式
## standard
每次启动Activity，都会创建一个新的Activity的实例，并加入到任务栈中。
## singleTop(栈顶复用)
如果栈顶已经存在要创建的Activity，就会复用这个Activity。
## singleTask(栈内复用)
这是一种单例模式，会检测当前任务栈中是否存在要创建的Activity，如果存在就将这个实例之上的Activity出栈，使要创建的Activity重新位于栈顶。这时候会回调一个onNewIntent()方法。
## singleInstance
这个Activity在整个系统中有且只有一个实例，它独享一个任务栈。
# 四.Scheme跳转协议
Scheme是一种页面内跳转协议，是一种非常好的实现机制，通过定义自己的Scheme协议，可以非常方便的跳转App的各个页面；通过Scheme协议，服务器可以定制化告诉App跳转哪个页面，可以通过通知栏消息定制化跳转页面，可以通过H5页面跳转页面等。
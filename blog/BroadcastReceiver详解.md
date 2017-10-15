BroadcastReceiver详解.md
# 1. 广播

## 1.1 广播的定义
在Android中，Broadcast是一种广泛运用的在应用程序之间传输信息的机制，Android中我们要发送的广播内容是一个Intent，这个Intent中我们可以携带我们要传送的数据。
广播实现了不同程序间的数据传输与共享。
广播可以实现通知的作用。

## 1.2 广播的场景
同一App内具有多个进程的不同组件之间的消息通信。
不同App之间组件之间消息通信。

## 1.3 广播的种类
Normal Broadcast: Context.sendBroadcase
System Broadcase: Context.sendOrderedBroadcase
Local Broadcase: 只在自身App内传播

# 2. 实现广播-Receiver

## 2.1 静态注册：注册完成后就一直运行

## 2.2 动态注册：跟随Activity的生命周期

## 2.3 区别
静态注册：
在清单文件中声明BroadcastReceiver。
BroadcastReceiver不受Activity生命周期的影响，Activity被销毁，BroadcastReceiver可以收到广播，即使应用进程被杀死，BroadcastReceiver仍然能够接受到广播。
动态注册：
在代码中调用BroadcastReceiver来进行注册的。
BroadcastReceiver会收到Activity生命周期的影响，当Activity被销毁了，BroadcastReceiver也就被回收了。

# 3. 广播实现机制

    自定义广播接受者BroadcastReceiver，并重新onReceive()方法；
    通过Binder机制想AMS（Activity Manager Service）进行注册；
    广播发送者通过Binder机制向AMS发送广播；
    AMS查找符合相应条件（IntentFilter/Permission等）的BroadcastReceiver，将广播发送到BroadcastReceiver（一般情况下是Activity）相应的消息循环队列中；
    消息循环执行拿到此广播，回调BroadcastReceiver中的onReceive()方法。

# 4. LocalBroadcastManager详解

    使用它发送的广播将只在自身App内传播，因此不必担心泄漏隐私数据
    其它App无法对你的App发送该广播，因为你的App根本就不可能接收到非自身原因发送的该广播，因此不必担心有安全漏洞可以利用
    比系统的全局广播更加高效

    LocalBroadcastManager高效的原因主要是因为它内部是通过Handler实现的，它的sendBroadcast()方法含义并非和我们平时所用的一样，它的sendBroadcast()方法其实是通过handler发送一个Message实现的
    既然它内部是通过Handler来实现广播的发送的，那么相比与其他系统广播通过Binder实现那肯定是更高效了，同时使用Handler来实现，别的应用无法向我们的应用发送该广播，而我们应用内发送的广播也不会离开我们的应用
    LocalBroadcastManager内部协作主要是靠这两个Map集合：mReceivers和mActions，当然还有一个List集合mPendingBroadcasts，这个主要就是存储待接收的广播对象。
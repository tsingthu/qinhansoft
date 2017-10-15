Service面试详解.md
# 1. Service的应用场景

## 1.1 Service基础

### 1.1.1 Service是什么？
Service是一个一种可以在后台执行长时间运行操作而没有用户界面的应用组件。
Service可以由其它应用组件（如：Activity、Broadcast）启动，启动后Service就一直运行在后台，并且即使启动它的组件被销毁了，Service也不会受到影响。
Service是运行在主线程中，不能做耗时操作。

### 1.1.2 Service和Thread的区别
A.定义 
Thread是程序执行的最小单元，是分配CPU的最小单位。
Service是Android中的一种特殊机制，是运行在主线程中的。
B.实际开发 
Android中线程一般指的是工作线程，也就是后台线程；主线程是一种特殊的线程，负责UI的绘制。
Service是Android四大组件之一，它运行在主线程中，所以不能做耗时操作。
C.应用场景 
当需要做如网络请求、文件数据查询等耗时操作时，需要开启子线程。
需要长时间在后台运行且不需要UI时，需要开启Service。

# 2. 开启Service的两种方式以及区别

## 2.1 startService()
通过Activity启动Service后，这个Service就会一直在后台运行，即使Activity被回收了，Service也不会受到影响，直到Service被stop。

    1.定义一个类继承Service
    2.在Manifest.xml文件中声明该Service
    3.使用Context的startService(Intent)方法启动Service
    4.不再使用时，调用stopService(Intent)方法停止该服务

## 2.2 bindService()

    1.创建BindService服务端，继承自Service，并在类中，创建一个实现IBinder接口的实例对象并提供公共方法供客户端调用
    2.从onBind()回调方法返回此IBinder实例
    3.在客户端中，从onServiceConnected()回调方法接收IBinder，并使用提供的方法调用绑定服务
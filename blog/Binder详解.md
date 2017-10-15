Binder详解.md
# 1. Linux内核的基础知识

## 1.1 进程隔离/虚拟地址空间

## 1.2 系统调用

## 1.3 Binder驱动

# 2. Binder通信机制介绍

## 2.1 为什么使用Binder
Android使用的Linux内核拥有这非常多的跨进程通信机制
性能
安全

## 2.2 Binder通信模型
通讯录：Binder驱动
电话基站：ServiceManager

## 2.3 Binder通信机制原理

# 3. AIDL

## 3.1 到底什么是Binder
通常意义下，Binder指的是一种通信机制
对于Server进程来说，Binder指的是Binder本地对象/对于Client来说，Binder指的是Binder代理对象
对于传输过程而言，Binder是可以进行跨进程传递的对象。

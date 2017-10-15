WebView详解.md
# 1. WebView常见的一些坑

> 1. Android API level 16以及之前的版本存在远程代码执行安全漏洞，该漏洞源于程序没有正确限制使用WebView.addJavascriptInterface()方法，远程攻击者可以通过使用Java Reflection API利用该漏洞执行任意Java对象的方法。
> 2. WebView在布局文件中的使用：WebView写在其他容器中时
> 3. jsbridge
> 4. WebViewClient.onPageFinished() ——> WebChromeClient.onProgressChanged()
> 5. 后台耗电
> 6. WebView硬件加速导致页面渲染问题

# 2. 关于WebView的内存泄漏问题

> 1. 独立进程，简单暴力，不过可能涉及到进程间通信。
> 2. 动态添加WebView，对传入WebView中使用的Context使用弱引用，动态添加WebView意思是在布局创建一个ViewGroup用来放置WebView，Activity创建时add进来，在Activity停止时remove掉。
# 避免Android中的内存泄漏

## Handler的泄漏
由于 Handler 属于 TLS(Thread Local Storage) 变量, 生命周期和 Activity 是不一致的，所以如果没有处理好是很容易造成内存泄漏的。
当Activity被销毁时，如果一个handler是在Activity内部声明的，且MessageQueue有尚未处理完的Message或者正在处理一个消息的操作比较耗时，这时仍会隐式持有Activity的引用。解决方法有以下几种方式:

- 将Handler声明为static类型，或者写一个外部类继承自Handler，这样就不会持有Activity的引用，如果需要使用Activity的引用，则传入Activity的弱引用，使得在Activity被销毁的时候能得到释放。
- 在Activity销毁时remove掉Message和Runnable。

## Bitmap泄漏
Bitmap一般都是通过BitmapFactory的工厂方法创建的，其内存分配在Java层和C层，Java层可在发生GC并且其实例没有任何引用的时候被回收，而C层则只能显式调用recycle方法进行回收。

## 各种连接泄漏
Cursor,socket,io连接及时进行关闭。

## 集合类中的内存泄漏
当某个对象被添加进集合中后，如果仅仅把自身置为null，那集合类仍会持有该对象的引用而不释放，在日常开发过程中往往会忘记调用clear方法，当持有一系列大对象时，内存泄漏也就会更加严重。

## 监听器泄漏
在开发过程中常常要对某些事件进行监听，会调用addXXXListener，然而调用完后没有在合适的时间把它remove掉，这样也会造成泄漏。

## 订阅者注册泄漏
常见的有EventBus注册，RxJava的各种订阅，在Activity被Destory时记得取消订阅注册。

## 动画
使用属性动画在不用的时候记得停止。

## 匿名内部类
匿名内部类会隐式地持有Activity的引用，因此在日常开发中要注意当Activity被销毁时各个匿名内部类是否还会继续执行内部的操作，有的话要将匿名内部类的生命周期与Activity的生命周期分开，或者写个外部类。

## WebView的内存泄漏
WebView占用内存比较大，而且如果不处理好的话将很有可能导致内存泄漏，具体解决内存泄漏的做法如下：
- 不要在xml声明WebView，而是在代码中new
- 在Activity被销毁的时候及时对webview进行回收，包括关闭Js,从父ViewGroup里面remove掉WebView，remove掉WebView内部的view。
- 如果存在某些机型不兼容以上几种解决方案的可以采用另开启一个进程的方式，在WebView结束的时候销毁这个进程。

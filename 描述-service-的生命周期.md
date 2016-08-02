# 描述 Service 的生命周期

Service 有

* 绑定模式
* 非绑定模式

不同的模式生命周期不同

![Service 生命周期](service-生命周期.png)






非绑定模式： 当第一次调用startService 的时候执行的方法依次为onCreate() 、

onStartCommand()，当Service 关闭的时候调用onDestory 方法。

绑定模式：第一次bindService（）的时候，执行的方法为onCreate()、onBind(）解除绑定的

时候会执行onUnbind()、onDestory()。

上面的两种生命周期是在相对单纯的模式下的情形。我们在开发的过程中还必须注意Service 实

例只会有一个，也就是说如果当前要启动的Service 已经存在了那么就不会再次创建该Service 当然

也不会调用onCreate（）方法。

一个Service 可以被多个客户进行绑定，只有所有的绑定对象都执行了onBind（）方法后该

Service 才会销毁，不过如果有一个客户执行了onStart()方法，那么这个时候如果所有的bind 客户

都执行了unBind()该Service 也不会销毁。


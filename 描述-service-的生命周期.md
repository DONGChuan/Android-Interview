# 描述 Service 的生命周期

Service 有

* 绑定模式
* 非绑定模式

不同的模式生命周期不同

![Service 生命周期](service-生命周期.png)

我们在开发的过程中还必须注意 **Service 实例只会有一个**, 也就是说如果当前要启动的 Service 已经存在了那么就不会再创建该 Service 当然也就不会调用 `onCreate()`.

但是如果是绑定模式, 一个 Service 可以被多个客户进行绑定, 只有所有的绑定对象都执行了`onUnbind()` 方法后该服务才回销毁.



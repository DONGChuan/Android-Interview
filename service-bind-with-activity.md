# **Activity 怎么和 Service 绑定? **

Activity 通过 `bindService(Intent service, ServiceConnection conn, int flags)` 跟服务 进行绑定, 当绑定成功的时候服务会将代理对象通过  `onBind()` 方法传给 conn, 这样我们就拿到了服务提供的服务代理对象.


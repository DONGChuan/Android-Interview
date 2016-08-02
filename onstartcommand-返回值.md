# onStartCommand 返回值

`onStartCommand()` 方法返回整型数来描述系统应该**如何在服务终止的情况下继续运行服务**.

返回的值必须是以下常量之一:

* START_STICKY 

如果服务在开始后 (`onStartCommand()` 返回后) 被终止, 比如内存不足, 然后会保持已开始状态 (started state), 但是并不保留接收的 intent. 稍后当系统有足够内存时会自己尝试重新创建服务. 因为服务仍处于已开始状态, 所以重建后会调用 `onStartCommand()` 方法. **但是除非此时有挂起的 intent 要启动服务, 不然传递的 intent 为 null.** 使用此方式需要在代码中考虑处理 null 的情况.

该模式主要用于可以在任意的时间段显示的开始和结束服务, 比如后台的音乐播放服务. 

* START_NOT_STICKY 

如果服务在开始后 (`onStartCommand()` 返回后) 被终止, 但是不会保持已开始状态. 系统也不会再自建该服务. 只能通过显示的调用 `startService(Intent)` 来重新创建服务. 这是最安全的选项, 可以**避免在不必要时以及应用能够轻松重启所有未完成的作业时运行服务**.

* START_REDELIVER_INTENT 

如果服务在开始后 (`onStartCommand()` 返回后) 被终止, 则会重建服务, 并且传入最后一个接收的 intent 到 `onStartCommand()`. 这适用于主动执行应该立即恢复的服务(例如下载文件).

小结:

* `START_STICKY`, `START_REDELIVER_INTENT` 会重启服务
* `START_STICKY` 会传递 null 的 intent
* `START_REDELIVER_INTENT` 会传递最后一个 intent

#### 来源

* [Service 学习笔记](http://dongchuan.github.io/android/2016/06/24/Android-Service.html)

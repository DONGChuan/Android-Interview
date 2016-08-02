# 什么是 IntentService

IntentService 是用来处理异步 (asynchronous) 请求的 Service 的子类. 但是是通过创建一个独立的工作者线程 (worker thread) 来完成工作. 并且在完成工作后自动关闭服务. 

通常的 Service 是用于无需 UI 的任务. 但是不能执行耗时任务. 不然的话需要创建额外的线程来执行任务. 所以就有了 IntentService. 它主要被用于处理耗时任务的服务, 自身内部会自动创建一个额外的线程来执行任务. 

#### 来源

* [IntentService 学习笔记](http://dongchuan.github.io/android/2016/06/14/Android-IntentService.html)



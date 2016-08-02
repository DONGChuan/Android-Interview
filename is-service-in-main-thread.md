# **Service 能否在主线程中执行? **

Service 是在主线程中调用的,

# **service 里面是否能执行耗时的操作?**

 不行.  耗时操作会阻塞UI. 可以使用创建一个新的线程或者使用`IntentService`. 

# Service 和 Activity 在同一个线程吗?

对于同一 app 来说默认情况下是在同一个线程中的 main Thread (UI Thread)





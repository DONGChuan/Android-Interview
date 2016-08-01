# **Service 能否在主线程中执行? **

Service 是在主线程中调用的,

# **service 里面是否能执行耗时的操作?**

 不行.  耗时操作会阻塞UI. 可以使用创建一个新的线程或者使用`IntentService`. 




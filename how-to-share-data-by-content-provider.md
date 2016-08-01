# **ContentProvider 是如何实现数据共享的**

在 Android 中如果想将自己应用的数据\(一般多为数据库中的数据\)提供给第三发应用, 那么我们只能通过 ContentProvider 来实现.

 

ContentProvider 是应用程序之间共享数据的接口. 使用的时候首先自定义一个类继承 ContentProvider, 然后覆写 query、insert、update、delete 等方法. 因为其是四大组件之一因此必须在 AndroidManifest 文件中进行注册. 把自己的数据通过 uri 的形式共享出去 



第三方可以通过 ContentResolver 来访问该 Provider


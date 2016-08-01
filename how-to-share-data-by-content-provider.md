# **ContentProvider 是如何实现数据共享的**

在 Android 中如果想将自己应用的数据\(一般多为数据库中的数据\)提供给第三发应用, 那么我们只能通过 ContentProvider 来实现.

ContentProvider 是应用程序之间共享数据的接口. 使用的时候首先自定义一个类继承 ContentProvider, 然后覆写 query、insert、update、delete 等方法. 因为其是四大组件之一因此必须在 AndroidManifest 文件中进行注册. 把自己的数据通过 uri 的形式共享出去

第三方可以通过 ContentResolver 来访问该 Provider

## **URI 介绍**

 每一个 ContentProvider 都拥有一个公共的URI, 只能通过访问该 URI 来获得数据.

Android所提供的ContentProvider都存放在android.provider包中。 将其分为A，B，C，D 4个部分： 

A：标准前缀, 用来说明一个 Content Provider 控制这些数据，无法改变: "content:\/\/" 

B：URI 的标识，用于唯一标识这个ContentProvider, 外部调用者可以根据这个标识来找到它. 它定义了是哪个Content Provider提供这些数据. 对于第三方应用程序，为了保证URI标识的唯一性，它必须是一个完整的、小写的类名. 这个标识在 元素的 authorities属性中说明：一般是定义该 ContentProvider 的包.类的名称 

C：路径（path），通俗的讲就是你要操作的数据库中表的名字, 或者你也可以自己定义, 记得在使用的时候保持一致就可以了；"content:\/\/com.bing.provider.myprovider\/tablename" 

D：如果URI中包含表示需要获取的记录的ID；则就返回该id对应的数据，如果没有ID，就表示返回全部； "content:\/\/com.bing.provider.myprovider\/tablename\/\#" \#表示数据id.


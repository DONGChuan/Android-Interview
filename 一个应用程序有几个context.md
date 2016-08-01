# **一个应用程序有几个Context**

在应用程序中Context的具体实现子类就是: Activity, Service, Application. 那么`Context数量 = Activity数量 + Service数量 + 1`

> Broadcast Receiver, Content Provider 并不是 Context 的子类, 它们所持有的 Context 都是其他地方传过去的, 所以并不计入Context总数.


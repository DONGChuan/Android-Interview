# 请解释下在单线程模型中Message、Handler、MessageQueue、Looper之间的关系


* Message: 是 Handler 接收和处理的消息对象
* Looper: 每个线程只能有一个 Looper. 它的 loop 方法负责读取 MessageQueue 中的消息, 读到消息之后就把消息交给发送该消息的 Handler 进行处理.
* MessageQueue: 消息队列. 它采用先进先出的方式来管理 Message. 程序创建 Looper 对象时, 会在它的构造器中创建 MessageQueue 对象.
* Handler: 在新启动的线程中发送消息, 在主线程中获取处理消息.

当新启动的线程发送消息时, 消息会发送到与之关联的 MessageQueue, 而 Handler 会不断地从 MessageQueue 中获取并处理消息. 这将导致 Handler 类中处理消息的方法被回调. 这个方法处于主线程, 从而更新 UI.


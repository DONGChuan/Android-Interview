# **Context, Activity, Appliction 有什么区别?**

### 相同:

Activity 和 Application 都是 Context 的子类

Context 从字面上理解就是上下文的意思, 在实际应用中它也确实是起到了管理上下文环境中各个参数和变量的作用, 方便我们可以简单的访问到各种资源.

### 不同:

维护的生命周期不同.

* Activity 维护的是当前的 Activity 的生命周期.** 所以其对应的Context也只能访问该 Activity 内的各种资源**

* Application 维护的是整个项目的生命周期.


使用 context 的时候, 小心内存泄露, 防止内存泄露, 注意一下几个方面:

1. 不要让生命周期长的对象引用 activity context, 即保证引用 activity 的对象要与 activity 本身生命周期是一样的.
2. 对于生命周期长的对象,可以使用 application context。
3. 避免非静态的内部类, 尽量使用静态类, 避免生命周期问题, 注意内部类对外部对象引用导致的生命周期变化.


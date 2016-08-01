# Serializable 和 Parcelable 的区别

1. 在使用内存的时候, Parcelable 类比 Serializable 性能高, 所以推荐使用 Parcelable 类

2. Serializable 在序列化的时候会产生大量的临时变量, 从而引起频繁的 GC.

3. Parcelable 不能使用在要将数据存储在磁盘上的情况. 尽管 Serializable 效率低点, 但在这种情况下, 还是建 

  议你用 Serializable


### 如何用:

* Serializable 的实现, 只需要继承 Serializable 即可. 这只是给对象打了一个标记,系统会自动将其序列化.
* Parcelabel 的实现, 需要在类中添加一个静态成员变量 `CREATOR`, 这个变量需要继承 `Parcelable.Creator` 接口.


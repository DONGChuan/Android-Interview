# **如何保存 Activity 的状态**

**覆写 onSaveInstanceState\(\) 方法**

Activity 的状态通常情况下系统会自动保存的, 只有当我们需要保存额外的数据时才需要使用到这样的功能.

一般来说, 调用 `onPause()` 和 `onStop()` 方法后的 activity 实例仍然存在于内存中, activity 的所有信息和状态数据不会消失, 当 activity 重新回到前台之后, 所有的改变都会得到保留. 但是当系统内存不足时, 调用 `onPause()` 和 `onStop()` 方法后的 Activity 可能会被系统摧毁, 此时内存中就不会存有该 Activity 的实例对象了, 如果之后这个 Activity 重新回到前台, 之前所作的改变就会消失.

为了避免此种情况的发生, 需要覆写 `onSaveInstanceState()` 方法. `onSaveInstanceState()` 方法接受一个 Bundle 类型的参数, 开发者可以将状态数据存储到这个 Bundle 对象中, 这样即使 Activity 被系统摧毁, 当用户重新启动这个 Activity 而调用它的 onCreate\(\)方法时, 上述的 Bundle 对象会作为实参传递给 `onCreate()` 方法, 开发者可以从 Bundle 对象中取出保存的数据, 然后利用这些数据将 activity 恢复到被摧毁之前的状态.

需要注意的是, `onSaveInstanceState()` 方法并不是一定会被调用的, 因为有些场景是不需要保存状态数据的. 比如用户按下 BACK 键退出 Activity 时, 用户显然想要关闭这个 Activity, 此时是没有必要保存数据以供下次恢复的, 也就是 `onSaveInstanceState()` 方法不会被调用. 如果调用 `onSaveInstanceState()` 方法, 调用将发生在 `onPause()` 或 `onStop()` 方法之前.


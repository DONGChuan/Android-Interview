# 生命周期

* 启动: onCreate()—>onStart()—>onResume(), Activity进入运行状态.
* 退居后台: 当前Activity转到新的Activity界面或按Home键回到主屏: onPause()—>onStop(), 进入停滞状态.
* 返回前台: onRestart()—>onStart()—>onResume(), 再次回到运行状态.
* Activity 退居后台, 且系统内存不足, 系统会杀死这个后台状态的 Activity (此时这个Activity引用仍然处在任务栈中，只是这个时候引用指向的对象已经为null), 若再次回到这个Activity, 则会走onCreate()–>onStart()—>onResume()(将重新走一次Activity的初始化生命周期)
* 锁定屏与解锁屏幕, 只会调用onPause(), 而不会调用onStop()方法, 开屏后则调用onResume()
* 当 Activity 被另一个透明或者 Dialog 样式的 Activity 覆盖时就会 onPause. 这时它仍然可见. 只是失去焦点, 不可与用户交互.

![Activity 生命周期](activity-生命周期.png)

### 可能的问题

* 画生命周期图
* `onStart()` 与 `onResume()` 有什么区别?

> `onStart()` 方法在 `onCreate()` 方法之后被调用或者在 Activity 从 Stop 状态转换为 Active 状态时被调用, 一般执行了 `onStart()` 后就执行 `onResume()` 
> 
>`onResume()` 在 Activity 从 Pause 状态转换到 Active 状态时被调用. 使 Activity 获得用户焦点, 可以再与用户交互.


来源:
* [Activity生命周期](https://github.com/GeniusVJR/LearningNotes/blob/master/Part1/Android/Android%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.md)
# 生命周期

* 启动: onCreate()—>onStart()—>onResume(), Activity进入运行状态.
* 退居后台: 当前Activity转到新的Activity界面或按Home键回到主屏: onPause()—>onStop(), 进入停滞状态.
* 返回前台: onRestart()—>onStart()—>onResume(), 再次回到运行状态.
* Activity 退居后台, 且系统内存不足, 系统会杀死这个后台状态的 Activity (此时这个Activity引用仍然处在任务栈中，只是这个时候引用指向的对象已经为null), 若再次回到这个Activity, 则会走onCreate()–>onStart()—>onResume()(将重新走一次Activity的初始化生命周期)
* 锁定屏与解锁屏幕, 只会调用onPause(), 而不会调用onStop()方法, 开屏后则调用onResume()

![Activity 生命周期](activity-生命周期.png)

来源:
* [Activity生命周期](https://github.com/GeniusVJR/LearningNotes/blob/master/Part1/Android/Android%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.md)
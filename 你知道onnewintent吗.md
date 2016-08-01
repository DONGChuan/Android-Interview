# **你知道onNewIntent吗?**

只有启动模式是 singleTop 或者使用 `FLAG_ACTIVITY_SINGLE_TOP` 来 `startActivity(Intent)`. 这个方法才回被调用. 如果新 Activity 已经位于任务栈的栈顶, 那么此 Activity 不会被重新创建. 然是调用如下方法:

_onNewIntent--&gt;onRestart--&gt;onStart--&gt;onResume._


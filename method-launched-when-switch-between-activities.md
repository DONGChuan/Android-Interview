# **两个 Activity 之间跳转时必然会执行的是哪几个方法**

一般情况下比如说有两个 activity, 分别叫 A,B, 当在 A 里面激活 B 的时候, A 会调用 onPause\(\) 方法, 然后 B 调用 onCreate\(\)--&gt;onStart\(\)--&gt;onResume\(\). 这个时候 B 覆盖了窗体, A 会调用 onStop\(\) 方法. 如果 B 是个透明的或者是对话框的样式, 就不会调用 A 的 onStop\(\) 方法.


# 横竖屏切换时候Activity的生命周期

#### 总结:

1. 不设置 \`Activity\` 的 \`android:configChanges\` 时, 切屏会重新调用各个生命周期, 切横屏时会执行一次, 切竖屏时会执行两次.

2. 设置 \`Activity\` 的 \`android:configChanges="orientation"\` 时, 切屏还是会重新调用各个生命周期, 切横\/竖屏时只会执行一次.

3. 设置 \`Activity\` 的 \`android:configChanges="orientation\|keyboardHidden"\` 时, 切屏不会重新调用各个生命周期, 只会执行\`onConfigurationChanged\`方法


> Activity 会自己管理配置的变化. 当运行的时候, 配置变了, 它会自己关闭并重新启动, 但是如果设置了 android:configChanges="某一个配置", 它就不会在这个配置发生改变时重新启动.

#### 具体过程

1. 新建一个Activity，并把各个生命周期打印出来

2. 运行Activity，得到如下信息

  onCreate--&gt;onStart--&gt;onResume--&gt;

3. 切换成横屏时

  onSaveInstanceState--&gt;onPause--&gt;onStop--&gt;onDestroy--&gt;onCreate--&gt;onStart--&gt;onRestoreInstanceState--&gt;onResume--&gt;

4. 再切换成竖屏时，发现打印了两次相同的log

  onSaveInstanceState--&gt;onPause--&gt;onStop--&gt;onDestroy--&gt;onCreate--&gt;onStart--&gt;onRestoreInstanceState--&gt;onResume--&gt;onSaveInstanceState--&gt;onPause--&gt;onStop--&gt;onDestroy--&gt;onCreate--&gt;onStart--&gt;onRestoreInstanceState--&gt;onResume

5. 修改AndroidManifest.xml, 把该 Activity 添加 android:configChanges="orientation"

  onSaveInstanceState--&gt;onPause--&gt;onStop--&gt;onDestroy--&gt;onCreate--&gt;onStart--&gt;onRestoreInstanceState--&gt;onResume--&gt;

6. 再执行步骤4, 发现不会再打印相同信息, 但多打印了一行 onConfigChanged

  onSaveInstanceState--&gt;onPause--&gt;onStop--&gt;onDestroy--&gt;onCreate--&gt;onStart--&gt;onRestoreInstanceState--&gt;onResume--&gt;onConfigurationChanged--&gt;

7. 把步骤5的 android:configChanges="orientation" 改成 android:configChanges="orientation\|keyboardHidden"，执行步骤3, 就只打印onConfigChanged

  onConfigurationChanged--&gt;

8. 执行步骤4

  onConfigurationChanged--&gt;onConfigurationChanged--&gt;



# **如何退出 Activity? 如何安全退出已调用多个 Activity 的 Application?**

1. 通常情况用户退出一个 Activity 只需按返回键,我们写代码想退出 activity 直接调用 finish\(\) 方法就行.
2. **发送特定广播**: 在需要结束应用时, 发送一个特定的广播, 每个 Activity 收到广播后, 关闭即可.
  `//给某个 activity 注册接受接受广播的意图 registerReceiver(receiver, filter)`
  `//如果接受到的是 关闭 activity 的广播 activity finish()掉`
3. 递归退出 就调用 finish\(\)方法 把当前的在打开新的 Activity 时使用 startActivityForResult, 然后自己加标志, 在 onActivityResult 中处理, 递归关闭.
4. 其实也可以通过 intent 的 flag 来实现 intent.setFlags\(Intent.FLAG\_ACTIVITY\_CLEAR\_TOP\)激活一个新的 activity。 此时如果该任务栈中已经有该 Activity, 那么系统会把这个 Activity 上面的所有 Activity 干掉. 其实相当于给 Activity 配置的启动模式为 SingleTop.
5. 记录打开的 Activity: 每打开一个 Activity, 就记录下来. 在需要退出时, 关闭每一个 Activity

List&lt;Activity&gt; lists ;\/\/ 在 application 全局的变量里面 lists = new ArrayList&lt;Activity&gt;\(\); 

lists.add\(this\); 

for\(Activity activity: lists\) { 

activity.finish\(\); 

} 

lists.remove\(this\);






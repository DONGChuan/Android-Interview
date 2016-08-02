# Service 里面可以弹 Toast 么

可以. 使用 Toast 需要有一个 Context, 而 Service 本身就是 Context 的子类. 因此在 Service 里使用 Toast 完全可以的.

经常见到的情况就是在 Service 中完成下载任务后可以弹 Toast 通知用户.


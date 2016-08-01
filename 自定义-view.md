
这里我们先简单理解 View 的绘制:

1. 测量 `onMeasure()` 决定View的大小
2. 布局 `onLayout()` 决定View在ViewGroup中的位置
3. 绘制 `onDraw()` 如何绘制这个View

### 自定义View的分类

* 继承View
* 继承ViewGroup
* 继承系统控件(Button,LinearLayout…)

自定义View的过程
http://blog.csdn.net/vfush/article/details/51613265
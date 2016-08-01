# **getWidth\(\)和getMeasuredWidth\(\)的区别**

getMeasuredWidth\(\): 只要一执行完 `setMeasuredDimension()`方法, 就有值了, 并且不再改变.

getWidth\(\): 必须执行完 `onMeasure()` 才有值, 可能发生改变. 

如果 onLayout 没有对子 View 实际显示的宽高进行修改, 那么 getWidth\(\) 的值 == getMeasuredWidth\(\) 的值.


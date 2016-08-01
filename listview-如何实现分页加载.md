# **ListView 如何实现分页加载**

设置 ListView 的滚动监听器 `setOnScrollListener(new OnScrollListener{….})` 

在监听器中有两个方法: 滚动状态发生变化的方法` onScrollStateChanged`和 listView 被滚动时调用的方法`onScroll`


在滚动状态发生改变的方法中,有三种状态: 
* 手指按下移动的状态: SCROLL\_STATE\_TOUCH\_SCROLL: \/\/ 触摸滑动 
* 惯性滚动: SCROLL\_STATE\_FLING: \/\/ 滑翔
* 静止状态: SCROLL\_STATE\_IDLE: \/\/ 静止

对不同的状态进行处理: 



分批加载数据,只关心静止状态: 关心最后一个可见的条目, 如果最后一个可见条目就是数据适配器\(集合\)里的最后一个, 此时可加载更多的数据. 在每次加载的时候, 计算出滚动的数量, 当滚动的数量大于等于总数量的时候, 可以提示用户无更多数据.


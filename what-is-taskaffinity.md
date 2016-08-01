# TaskAffinity 是什么?

Activity 的归属, 也就是 Activity 应该在哪个 Task 中. 一般情况下在同一个应用中, 启动的 Activity 都在同一个 Task 中.



每个 Activity 都有 taskAffinity 属性, 这个属性指出了它希望进入的 Task. 如果一个 Activity 没有显式的指明taskAffinity, 那么它就会使用 Application 的 taskAffinity, 如果 Application 也没有指明, 那么该 taskAffinity 的值就等于包名. 


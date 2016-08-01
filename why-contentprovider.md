# 为什么要用 ContentProvider

ContentProvider 屏蔽了数据存储的细节, 内部实现对用户完全透明, 用户只需要关心操作数据的 uri 就可以了, ContentProvider 可以实现不同 app 之间共享.

# 它和 sql 的实现上有什么差别?

Sql 也有增删改查的方法,但是 sql 只能查询本应用下的数据库. 而 ContentProvider 还可以去增删改查本地文件. xml 文件的读取等.


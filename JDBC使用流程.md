### JDBC 使用流程

1.注册驱动 

​	这一步可以省略，通过加载加载driver的全限定类名。driver中的静态代码块里面有注册驱动的方法

2.获取连接对象

​	获取connection对象有三要素：URL ROOT PASSWORD 

3编写sql语句

​	编写需要执行的sql语句

​	如果该语句是进行预编译执行，那么在编写的时候对于要传入的内容用？替代。

4.获取执行sql对象 statement

​	获取statement对象，该对象是普通的statement对象，不能防止sql注入问题。

​	一般获取prepareStatement对象，在获取对象的时候将sql语句传递进去，

​	prepareStatement可以防止sql注入：通过对传入的sql语句中的敏感字符进行转义，使其表示原有的意思

​	还能进行预编译：预编译功能需要手动开启，URL中添加?useServerPrepStmts=true

5执行sql语句

如果使用普通的statement，执行语句的时候传入sql语句

如果使用prepareStatement，执行sql的时候不需要传入sql语句了，但是先需要设置值，替换sql中？

设置用setXxx方法进行设置

6处理结果

根据执行的结构进行逻辑判断

查询语句返回的时候resultSet，是一个集合，

该集合中next()方法，初始值指向标题，next方法执行过后，会向下移动一行，如果有这一行有数据则返回true，反之FALSE；

集合有getXxx方法可以获取结果

7释放资源


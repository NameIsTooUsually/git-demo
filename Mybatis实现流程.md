### ==Mybatis实现流程==

1创建User表，添加数据 //在数据库中创建一个表存储数据
2创建模块，导入坐标	//在创建好的pom.xml配置文件中添加依赖的坐标（导入MyBatis的jar包，以及需要使用的jar相关jar包）
3编写MyBatis核心配置文件-->替换连接信息，解决硬编码问题	//在模块的resource目录下创建MyBatis的配置文件mybatis-config.xml
4编写Sql映射文件-->统一管理sql语句，解决硬编码问题	//在resource目录下创建映射配置文件UserMapper.xml
5编码
	1定义pojo类  //该类将查询的结果封装起来
	2加载核心配置文件，获取SqlSessionFactory对象
	3获取sqlSession对象，执行sql语句 也可以使用Mapper代理的方式执行
	4释放资源

### ==Mapper代理==

​	使用Mapper代理的条件
​	1创建一个与Mapper配置文件同名的接口该接口与Mapper配置文件放在同一个目录下
​		可以在resource目录下创建一个跟接口同结构的文件夹，将Mapper配置文件放进去
​	2设置Mapper配置文件的namespace属性为Mapper接口全限定类名
​	3在Mapper中定义方法，方法名就是sql映射文件中sql语句的id，并保持参数类型和返回值类型一致
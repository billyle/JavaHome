### mybatis
1.  mybatis 中 #{}和 ${}的区别是什么？
    #{}是预编译占位符，会进行类型转换和SQL注入防护；${}是字符串替换，直接拼接SQL，有SQL注入风险。
2.  什么是SQL注入 ，如何避免。
    SQL注入是攻击者通过拼接SQL语句来执行恶意代码。避免方法：使用预编译语句（如MyBatis的#{}），对用户输入进行校验和过滤。
3.  说一下 mybatis 的一级缓存和二级缓存
    一级缓存是SqlSession级别的，默认开启；二级缓存是Mapper级别的，需要配置开启，多个SqlSession共享。
4.  mybatis 是否支持延迟加载？延迟加载的原理是什么？
    支持。原理是在需要时通过AOP动态生成实现类，调用时再去加载关联数据。
5.  mybatis 动态sql中使用<where>标签与直接写where关键字有什么区别？
    <where>标签会自动判断条件是否存在，自动添加WHERE关键字，并处理多余AND/OR；直接写WHERE需要手动处理。
6.  mybatis 动态sql标签中循环标签中有哪些属性，各自的作用。
    <foreach>标签有collection（集合）、item（元素别名）、index（索引别名）、open（开始符号）、separator（分隔符）、close（结束符号）等属性。
7.  mybatis 和 hibernate 的区别有哪些？
    MyBatis是半自动ORM，需要手动编写SQL；Hibernate是全自动ORM，自动生成SQL。MyBatis更灵活，Hibernate更方便。
8.  RowBounds是一次性查询全部结果吗？为什么？
    是的。RowBounds通过内存分页实现，底层还是一次性查了所有数据，在Java层面进行截取。
9.  MyBatis 定义的接口，怎么找到实现的？
    通过接口的全限定名在Mapper.xml中查找对应的SQL语句作为实现。
10. Mybatis的底层实现原理。
    通过反射、动态代理、OGNL表达式等技术，将Java对象与SQL语句进行映射，执行数据库操作。
11. Mybatis是如何进行分页的？分页插件的原理是什么？
    可以通过RowBounds或SQL语句（如limit）分页。分页插件通过拦截器拦截SQL，在SQL后添加limit语句实现。
12. Mybatis执行批量插入，能返回数据库主键列表吗？
    可以，通过配置useGeneratedKeys="true"和keyProperty指定主键字段。
13. Mybatis都有哪些Executor执行器？它们之间的区别是什么？
    SimpleExecutor（简单执行器）、ReuseExecutor（可重用Statement执行器）、BatchExecutor（批处理执行器）、ReuseExecutor（可重用Statement执行器）、CachingExecutor（缓存执行器）。区别在于Statement的重用、批处理和缓存策略不同。
14. Mybatis动态sql有什么用？执行原理？有哪些动态sql？
    动态SQL用于根据不同条件拼接SQL语句。原理是MyBatis在运行时根据传入参数，通过OGNL表达式解析XML中的标签，动态生成SQL。标签有<if>、<choose>、<when>、<otherwise>、<foreach>、<trim>、<where>、<set>等。
15. mybatis有几种分页方式？
    常见的有RowBounds分页、物理分页（SQL语句limit）、分页插件分页。
16. MyBatis框架的优点和缺点
    优点：SQL灵活，学习曲线平缓，性能较好。缺点：需要编写SQL，对复杂查询维护性稍差。
17. 使用MyBatis框架，当实体类中的属性名和表中的字段名不一样 ，怎么办 ？
    可以通过resultMap标签进行字段与属性的映射，或者在SQL中使用别名。
18. 通常一个Xml映射文件，都会写一个Dao接口与之对应，请问，这个Dao接口的工作原理是什么？Dao接口里的方法，参数不同时，方法能重载吗？
    工作原理是通过接口的全限定名找到对应的Mapper.xml文件执行SQL。接口方法不能重载，MyBatis通过方法名和参数类型区分方法。
19. Xml映射文件中，除了常见的select|insert|updae|delete标签之外，还有哪些标签？
    还有<resultMap>、<sql>、<insert>、<update>、<delete>、<select>、<if>、<choose>、<when>、<otherwise>、<foreach>、<trim>、<where>、<set>等。
20. 简述Mybatis的插件运行原理，以及如何编写一个插件。
    原理：MyBatis通过动态代理生成Mapper接口的代理对象，插件通过实现Interceptor接口，在intercept方法中拦截Executor、StatementHandler、ParameterHandler、ResultSetHandler等对象的特定方法，进行增强处理。编写插件需要实现Interceptor接口，重写intercept、plugin、setProperties方法，并在配置文件中注册。
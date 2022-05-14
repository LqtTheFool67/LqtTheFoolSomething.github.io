#### 了解Mybatis的缓存吗？

#### 一、简介

##### 1.什么是缓存？

存在内存中的临时数据
将用户经常查询的数据放在缓存(内存)中，用户去查询数据就不用从磁盘上(关系型数据库数据文件)查询，从缓存中查询，从而提高查询效率，解决了高并发系统的性能问题。

##### 2.为什么使用缓存？

减少和数据库的交互次数，减少系统开销，提高系统效率

##### 3.什么时候使用缓存？

经常查询并且不经常改变的数据适合使用缓存
反之，不经常查询且经常改变的数据不适合使用缓存



#### 二、缓存分类

##### 1.一级缓存

一级缓存是mybatis默认开启的缓存，我们不用自己去开启。它是SqlSession级别(一个sql语句中)的缓存也称为本地缓存，当调用SqlSession的修改，添加，删除，commit()，close()，clearCache()等方法时，就会清空一级缓存

一次查询的结果，给他暂存在缓存(内存)中，我们再去查询相同的数据时候就可以直接走缓存，就不用走数据库了。



##### 2.二级缓存

二级缓存是namespace级别(一个mapper映射文件)的缓存（也就是在同一个mapper下都会生效），需要我们手动开启和配置
注意：二级缓存只有在一级缓存死掉才可以执行

如何配置二级缓存？（主配置全文件可在主页mybtais文件夹中找到）

先在mybatis.xml（主配置文件）的settings标签中添加<setting name="cacheEnabled" value="true"/>
在mapper.xml（sql映射文件中）的mapper标签中添加<cache/> 标签
如何开启二级缓存？

在你想用二级缓存的语句标签中添加useCache="true"





https://blog.csdn.net/weixin_45472409/article/details/115428200?ops_request_misc=&request_id=&biz_id=102&utm_term=%E4%BA%86%E8%A7%A3mybatis%E7%BC%93%E5%AD%98%E5%90%97&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-115428200.142^v9^control,157^v4^control&spm=1018.2226.3001.4187
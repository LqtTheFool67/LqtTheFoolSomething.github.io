## 什么是聚合函数

**聚合函数作用于一组数据，并对一组数据返回一个值。**



![image-20220509115809212](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220509115809212.png)

**聚合函数类型**
**AVG()**
**SUM()**
**MAX()**
**MIN()**
**COUNT()**

**count(*)会统计值为 NULL 的行，而 count(列名)不会统计此列为 NULL 值的行。**



![image-20220509115915608](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220509115915608.png)



**过滤分组：HAVING子句**

1. **行已经被分组。**
2. **使用了聚合函数。**
3. **满足HAVING 子句中条件的分组将被显示。**
4. **HAVING 不能单独使用，必须要跟 GROUP BY 一起使用。**

**（使用having时。通常是对聚合函数后的列进行筛选。例如：sum(colum) >80）**



**WHERE和HAVING的对比**

**区别1：WHERE 可以直接使用表中的字段作为筛选条件，但不能使用分组中的计算函数作为筛选条件；**
**HAVING 必须要与 GROUP BY 配合使用，可以把分组计算的函数和分组字段作为筛选条件。**



**区别2：如果需要通过连接从关联表中获取需要的数据，WHERE 是先筛选后连接，而 HAVING 是先连接**
**后筛选。**



![image-20220509120448956](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220509120448956.png)



**查询的结构**

```Mysql
#方式1：
SELECT ...,....,...
FROM ...,...,....
WHERE 多表的连接条件
AND 不包含组函数的过滤条件
GROUP BY ...,...
HAVING 包含组函数的过滤条件
ORDER BY ... ASC/DESC
LIMIT ...,...
#方式2：
SELECT ...,....,...
FROM ... JOIN ...
ON 多表的连接条件
JOIN ...
ON ...
WHERE 不包含组函数的过滤条件
AND/OR 不包含组函数的过滤条件
GROUP BY ...,...
HAVING 包含组函数的过滤条件
ORDER BY ... ASC/DESC
LIMIT ...,...
#其中：
#（1）from：从哪些表中筛选
#（2）on：关联多表查询时，去除笛卡尔积
#（3）where：从表中筛选的条件
#（4）group by：分组依据
#（5）having：在统计结果中再次筛选
#（6）order by：排序
#（7）limit：分页
```


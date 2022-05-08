#### [1667. 修复表中的名字](https://leetcode-cn.com/problems/fix-names-in-a-table/)

```mysql
表： Users

+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| user_id        | int     |
| name           | varchar |
+----------------+---------+
user_id 是该表的主键。
该表包含用户的 ID 和名字。名字仅由小写和大写字符组成。
 

编写一个 SQL 查询来修复名字，使得只有第一个字符是大写的，其余都是小写的。

返回按 user_id 排序的结果表。

查询结果格式示例如下。

 

示例 1：

输入：
Users table:
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | aLice |
| 2       | bOB   |
+---------+-------+
输出：
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | Alice |
| 2       | Bob   |
+---------+-------+

```



```mysql
select user_id,concat(upper(left(name,1)),lower(substring(name,2))) as name
from Users
order by user_id;
```



#### **学习的点：**

**1.concat()**   **将多个[字符串](https://so.csdn.net/so/search?q=字符串&spm=1001.2101.3001.7020)连接成一个字符串。**

**			** **语法：concat(str1, str2,...) 返回结果为连接参数产生的字符串，如果有任何一个参数为null，则返回值为null******

**,left()**

​				**语法：执行成功后，从左边返回指定长度的字符串。****

**,substring()**

**			**语法：返回从指定位置到指定位置长度的字符串。*****
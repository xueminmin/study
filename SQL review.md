201# SQL 语法
- SQL structured query language
- select 列名，列名/*  from 库.表
- 不区分大小写，一般空格会被忽略
- 多条语句用；分隔，
- select distinct 列名，列名 from 表名   返回去重的列内容（distinct 作用于所有的列，相当对全部检索出的多列的内容去重，有一列的内容不同就不会被去掉）
- select top 5 列名 from 表名 适用于SQL SERVER /ACCESS 
- select 列名 from 表名 fetch first 5 row only  适用于DB2
- select 列名 from 表名 where rownum <=5 适用于oracle
- select 列名 from 表名  limit 5  适用于mysql mariaDB postgresql，SQLite
-  select 列名 from 表名 limit 5 offset XX     limit指定返回的行数，limit带的offset指定从哪开始，第一行是0，limit 1 offset 1 会检索第2行
- 注释 ： --行内注释 ；；#开头一整行都是注释；/*多行注释*/
- select 列名 from 表名 order by 列名（desc）  --order by 必须是最后一个子句，order by 后的列名没有必要出现在selcet中
- select 列名 from 表名 order by 列名1（desc），列名2（desc） 先按列名1排序，相同的按列名2 排序,desc作用于响应的列名之后
- select 列名 from 表名 where 条件（）
- select 列名 from 表名 where X between xx  and xx 包括开始和结束值
- select 列名 from 表名 where XX is null
- select 列名 from 表名 where XXXX and/or XXX
- select 列名 from 表名 where  x1 or x2 and x3 and的优先级比or高，先处理and 后处理or ，有需要的时候要加（）
- - select 列名 from 表名 where in ( , ,  , )
- select 列名 from 表名 where not xxx  不等于
- 利用通配符:适用于文本字段，使用like操作符
% 任何字段出现任意次数 select X fom X where x like 'XX%' 以xx开头  'xx% xx%'   'x%x'  
_ 任何字符出现一次，用法和%一致
注意ascess 数据库和%相同作用的是*  ， 和_ 相同作用的？
- 创建计算字段 +链接字段 字符都可以， as别名 ，字段和字段可以加减乘除
-使用函数：文本处理函数 left返回左边字符，right返回右边字符，length返回字符串长度，lower字符串转小写，ltrim去掉字符串左边的空格，rtrim去掉字符串右边的空格，upper字符串转为大写
- soundex 返回字符串的soundex值，将任意文本串转换为描述其语音表示的字母数字模式
select cust_name ,cust_contact from customers where soundex(cus_contact) =soundex('michael green')  这可以避免输入错误导致的查询不到
- 日期时间处理函数 datepart： select order-num from orders where datepart(yy,order-date) =2014 检索出2014年的订单  在oracle中没有datepart函数，
select order-num from orders where to_number(to_char(order_date,'YYYY')) =2014  ,to_char 提取日期成分 ，to_number 将提取的成分转换成数值以便和2014比较
- 使用between and 实现上述检索2014年的订单 select order-num from orders where order_date between to_date('01-01-2014')and to_date('12-31-2012')
- mysql 使用year函数提取年份，select order-num from orders where year（order_date） =2014
- 数值处理函数： abs 返回一个数的绝对值，，cos 返回一个角度的余弦，exp返回一个数的指数，pi返回圆周率，sin 返回一个角度的正弦，sqrt返回一个数的平方根，tan 返回一个角度的正切
- 汇总数据：avg 平均值，忽略null，count 计数，不管是不是null都计算，max最大值，min最小值，sum 求和；avg 和sum 可以使用distinct，比如avg（distinct 列名）表示只对不重复的求平均值
- 数据分组：group by 可包含任意数目的列，可以对分组进行嵌套，group by子句中列出的每一列都必须是检索列胡子和有效的表达式，但是不能是聚集函数。如果在select中使用表达式，必须在group by中指定相同的表达式。group by子句不能使用别名。除了聚集函数外，select语句中的每一列都必须在group by子句中给出。group by 在where 之后，order by 之前
- having ：使用同where ，where 在分组前过滤行，having 在分组后过滤分组
- 在where中子查询： select X FROM X where  X in (select X FROM X where  X ) 执行的时候从内向外处理，注意作为子查询的select 语句只能查询单个列
- 创建计算字段使用子查询： select cust_name , cust_state,(select count(*) from orders where orders.cust_id = customers.cust_id) as order from customers  （）内的子查询对每个查询出的cust_name 执行一次 ，需要使用完全限制列名
- 联结表 select x ,x,x, from x ,x ,where X.X = X.x 等值联结，也称内联结
- inner join:select x,x,x from X inner join X on X.x=X.x
- 联结多个表：  select x ,x,x, from x ,x，x where X.X = X.x AND  X.X = X.x AND  X.X = X.x
- 使用别名：select x ,x,x, from x as a ,x as b where a.X = b.x 
（oracle 不支持as ，省略as 即可制定别名）
- inner join 能对应上的，left out join 左边的表是全部 ，right out join 右边的表全部 ,full join 两个表全部
- 
 


 





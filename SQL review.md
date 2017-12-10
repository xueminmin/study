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
- inner join 能对应上的，left outer join 左边的表是全部 ，right outer join 右边的表全部 ,full outer join 两个表全部
- select x ,x from x  where x union select x, x from x where x === selct x from x where x or x   union每个查询必须有相同的列，表达式或者聚集函数，各个列没必要用相同的次序出现，列的数据类型必须兼容（类型不必完全相同，但是需要是可以隐含转换的，比如不同的日期类型，不同的数值类型）
- union 自动去除了重复的行，使用union all 会保留重复的行，where 实现不了union all 的功能
- 使用union 组合查询的时候，语句的最后可以使用一条order by 子句，对所有的子句进行排序，注意只能在最后使用一条order by ，不能在union 中的每个查询中使用
- union 还有两种类型:EXCEPT(有时候称作 MINUS)用于检索在第一个表中存在，第二个表中不存在的行；intersect 检索两个表中都存在的行。使用很少，因为利用join实现比较方便
- insert into table values('X','X',null,'X') 表中的每一列都必须给出，某列没有值的话需要用null，这样比较危险，建议指定列名后插入
- insert into table (列名，列名,列名) values （'x','x',null），值和列名一一对应，即使表的结构更改了，也不会影响使用，可以省略列，省略的列必须允许为空或者有默认值
- insert into table 1 (列名，列名) select （列名，列名） from table 2 where X 将查询结果插入另一个表中，select查询多少行就插入多少行，可以是0行;列名不需要对应，使用的是select 后列的位置来对应前面insert 的列名，第一列对应insert的第一个列名。
- select 列名  into 一个新的表 ，执行语句后创建的，有的也可以覆盖已经存在的表 from table;; mysql 等需要使用： creat table 表名 as select 列名 from table  任何select 选项和子句都可以使用，包括 where ，group by ，可以使用join从多个表中检索数据， 但是只能插入一个表中
- update 表名 set 列名= x，列名= x where x   注意必须要有where，否则会更新所有的行，可以set 列名 = null 来清空一个值
- delect from 表名 where x
- creat table 表名（注意必须是新的表名，不能更新已经存在的表）
- （ 列名 数据类型 not null default X， 列名 数据类型 null default x）  数据类型比如char（10） varchae（100），不指定null ，not null 一般是默认允许null，可以用指定默认的值来获取添加时间等时间戳，比如mysql 用 current_date()
- alter table 表名 add 列名 数据类型   altertable 表名 drop column  列名  alter table 在每种数据库中使用的方法不一致
- drop table 表名 永久的删除表，删除的时候没有确认，不可撤销，使用的时候要注意
- 使用视图简化SQL 查询，视图是虚拟的表，使用同表 create view 视图名称（必须是新的，不能和表名或者其他的视图名一致） as select x，x from xx where x and x 这里select 可以使用所有的语句 ，可以将多个表的复杂join做成一个视图，从而简化以后的查询，注意视图没有数据，每次使用的时候是吧select x from 视图的条件加到创建视图的条件上，所以基础表有变化的时候，视图检索出的数据也变化
-drop view 视图名称

  


 





# SQL 语法
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

 





### Hive
- (ETL封装好的分析工具，比如oracle和IBM提供的工具）
- hive将元数据存储在derby数据库（java编写的数据库），可以修改到mysql数据库
- hive是SQL解析引擎，将SQL 语句转换成M/R job ，提交到yarn然后在hadoop执行。
- hive的表对应hdfs的文件夹，hive表里的数据对应hdfs的文件
- creat （external外部的）table name(列名 属性，列名 属性。。。。）row format(格式) delimited（限定） fields terminated（结束） by '\t'
- hive语法中分；表示语句结束
- group by 语句和SQL 不一样，如果有 group by 语句，select 的字段要么在 group by 中，要么在聚合函数如 sum, avg 中
- 查分区表要加分区限制
- w3school 学习SQL语法

### Hive函数
- Hive中strict模式下限制：分区、order by、笛卡尔积

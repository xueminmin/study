### Hive
- (ETL封装好的分析工具，比如oracle和IBM提供的工具）
- hive将元数据存储在derby数据库（java编写的数据库），可以修改到mysql数据库
- hive是SQL解析引擎，将SQL 语句转换成M/R job ，提交到yarn然后在hadoop执行。
- hive的表对应hdfs的文件夹，hive表里的数据对应hdfs的文件
- creat （external外部的）table name(列名 属性，列名 属性。。。。）row format(格式) delimited（限定） fields terminated（结束） by '\t'

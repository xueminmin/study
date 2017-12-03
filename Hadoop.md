#### Hadoop
- Apache Hadoop:open-source software for reliable,scalable（可扩展的）,distributed分布式 computing.
- 解决海量数据存储 HDFS ； 海量数据分析 MapReduce("Map（映射）"和"Reduce（归约）");资源管理调度（yarn）
- Hadoop 擅长日志分析
- 版本：apache官方版本； cloudera（CDH）稳定 有商业支持，在apache基础上打了一些patch；HDP（hortonworks data platform）
- 去IOE化（oracla 数据库， IBM 小型机，EMC存储，为代表的集中存储计算）
- 云计算目前落到的技术就是虚拟化，硬件资源变成租赁云服务
- HDFS：hadoop distributed file system分布式文件系统
- YARN：yet another resource negotiator 资源管理调度系统
- mapreduce:分布式运算框架
- hdfs：namenode 管理元数据 ；datanode 存数据。优点：容量可以线性扩展；有副本机制，存储可控性高，吞吐量增大；有了namenode后，客户端访问文件就只需要指定hdfs上的路径
- hdfs实现机制：文件被切块存储在多台服务器是那个，存储的在各个服务器的本地文件系统钟；对于客户端说，不需要关心分布式细节，hdfs提供了抽象统一的目录树；对于每个文件块都有多个副本；hdfs中都文件和具体都实际存储位置之间都对应关系交由一个专门都服务器管理--namenode
- mapreduce：把运算往数据上移的思想。mapreduce的基本思想：1/将一个业务处理需求分成两个阶段来进行，map阶段和reduce阶段；2/将分布式计算中面临的公共问题封装成框架来实现（jia包的分发，任务的启动，任务的容错，调度，中间结果的分组传递。。。）；3/应用开发人员只需要关心业务逻辑。（mapreduce只是分布式运算的一种实现，类似的框架还有很多，比如storm（流式计算），spark（内存迭代计算）

vmware 虚拟机 

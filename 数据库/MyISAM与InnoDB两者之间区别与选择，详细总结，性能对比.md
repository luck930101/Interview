1、MyISAM：默认表类型，它是基于传统的ISAM类型，ISAM是Indexed Sequential Access Method (有索引的顺序访问方法) 的缩写，它是存储记录和文件的标准方法。不是事务安全的，而且不支持外键，如果执行大量的select，insert MyISAM比较适合。

2、InnoDB：支持事务安全的引擎，支持外键、行锁、事务是他的最大特点。如果有大量的update和insert，建议使用InnoDB，特别是针对多个并发和QPS较高的情况。



**一、表锁差异**

**MyISAM:**

myisam只支持表级锁，用户在操作myisam表时，select，update，delete，insert语句都会给表自动加锁，如果加锁以后的表满足insert并发的情况下，可以在表的尾部插入新的数据。也可以通过lock table命令来锁表，这样操作主要是可以模仿事务，但是消耗非常大，一般只在实验演示中使用。



**InnoDB ：**

Innodb支持事务和行级锁，是innodb的最大特色。

事务的ACID属性：atomicity,consistent,isolation,durable。

并发事务带来的几个问题：更新丢失，脏读，不可重复读，幻读。

事务隔离级别：未提交读(Read uncommitted)，已提交读(Read committed)，可重复读(Repeatable read)，可序列化(Serializable)

四种隔离级别的比较



| 读数据一致性及并发副作用 隔离级别 | 读数据一致性                   | 脏读 | 不可重复读 | 幻读 |
| --------------------------------- | ------------------------------ | ---- | ---------- | ---- |
| 为提交读(read uncommitted)        | 最低级别，不读物理上顺坏的数据 | 是   | 是         | 是   |
| 已提交读(read committed)          | 语句级                         | 否   | 是         | 是   |
| 可重复读(Repeatable red)          | 事务级                         | 否   | 否         | 是   |
| 可序列化(Serializable)            | 最高级别，事务级               | 否   | 否         | 否   |



 



查看mysql的默认事务隔离级别“show global variables like ‘tx_isolation’; ”



Innodb的行锁模式有以下几种：共享锁，排他锁，意向共享锁(表锁)，意向排他锁(表锁)，间隙锁。



注意：当语句没有使用索引，innodb不能确定操作的行，这个时候就使用的意向锁，也就是表锁



关于死锁：



什么是死锁？当两个事务都需要获得对方持有的排他锁才能完成事务，这样就导致了循环锁等待，也就是常见的死锁类型。



解决死锁的方法：



1、  数据库参数



2、  应用中尽量约定程序读取表的顺序一样



3、  应用中处理一个表时，尽量对处理的顺序排序



4、  调整事务隔离级别（避免两个事务同时操作一行不存在的数据，容易发生死锁）



**二、数据库文件差异**

**MyISAM ：**



myisam属于堆表



myisam在磁盘存储上有三个文件，每个文件名以表名开头，扩展名指出文件类型。



.frm 用于存储表的定义



.MYD 用于存放数据



.MYI 用于存放表索引



myisam表还支持三种不同的存储格式：



静态表(默认，但是注意数据末尾不能有空格，会被去掉)



动态表

压缩表

**InnoDB ：**

innodb属于索引组织表

innodb有两种存储方式，共享表空间存储和多表空间存储

两种存储方式的表结构和myisam一样，以表名开头，扩展名是.frm。

如果使用共享表空间，那么所有表的数据文件和索引文件都保存在一个表空间里，一个表空间可以有多个文件，通过innodb_data_file_path和innodb_data_home_dir参数设置共享表空间的位置和名字，一般共享表空间的名字叫ibdata1-n。



如果使用多表空间，那么每个表都有一个表空间文件用于存储每个表的数据和索引，文件名以表名开头，以.ibd为扩展名。



**三、索引差异**



1、关于自动增长



myisam引擎的自动增长列必须是索引，如果是组合索引，自动增长可以不是第一列，他可以根据前面几列进行排序后递增。



innodb引擎的自动增长咧必须是索引，如果是组合索引也必须是组合索引的第一列。



2、关于主键



myisam允许没有任何索引和主键的表存在，



myisam的索引都是保存行的地址。



innodb引擎如果没有设定主键或者非空唯一索引，就会自动生成一个6字节的主键(用户不可见)



innodb的数据是主索引的一部分，附加索引保存的是主索引的值。



3、关于count()函数



myisam保存有表的总行数，如果select count(*) from table;会直接取出出该值



innodb没有保存表的总行数，如果使用select count(*) from table；就会遍历整个表，消耗相当大，但是在加了wehre       条件后，myisam和innodb处理的方式都一样。



4、全文索引



myisam支持 FULLTEXT类型的全文索引



innodb不支持FULLTEXT类型的全文索引，但是innodb可以使用sphinx插件支持全文索引，并且效果更好。（sphinx   是一个开源软件，提供多种语言的API接口，可以优化mysql的各种查询）



5、delete from table



使用这条命令时，innodb不会从新建立表，而是一条一条的删除数据，在innodb上如果要清空保存有大量数据的表，最       好不要使用这个命令。(推荐使用truncate table，不过需要用户有drop此表的权限)



6、索引保存位置



myisam的索引以表名+.MYI文件分别保存。



innodb的索引和数据一起保存在表空间里。





**四、开发的注意事项**



1、可以用 show create table tablename 命令看表的引擎类型。



2、对不支持事务的表做start/commit操作没有任何效果，在执行commit前已经提交。



3、可以执行以下命令来切换非事务表到事务（数据不会丢失），innodb表比myisam表更安全：alter table tablename type=innodb;或者使用 alter table tablename engine = innodb;



4、默认innodb是开启自动提交的，如果你按照myisam的使用方法来编写代码页不会存在错误，只是性能会很低。如何在编写代码时候提高数据库性能呢？



a、尽量将多个语句绑到一个事务中，进行提交，避免多次提交导致的数据库开销。



b、在一个事务获得排他锁或者意向排他锁以后，如果后面还有需要处理的sql语句，在这两条或者多条sql语句之间程序应尽量少的进行逻辑运算和处理，减少锁的时间。



c、尽量避免死锁



d、sql语句如果有where子句一定要使用索引，尽量避免获取意向排他锁。



f、针对我们自己的数据库环境，日志系统是直插入，不修改的，所以我们使用混合引擎方式，ZION_LOG_DB照旧使用myisam存储引擎，只有ZION_GAME_DB，ZION_LOGIN_DB，DAUM_BILLING使用Innodb引擎。



**五、究竟该怎么选择**

下面先让我们回答一些问题：  

◆你的数据库有外键吗？  

◆你需要事务支持吗？  

◆你需要全文索引吗？  

◆你经常使用什么样的查询模式？  

◆你的数据有多大？  

myisam只有索引缓存  
innodb不分索引文件数据文件 innodb buffer  
myisam只能管理索引，在索引数据大于分配的资源时，会由操作系统来cache；数据文件依赖于操作系统的cache。innodb不管是索引还是数据，都是自己来管理  

思考上面这些问题可以让你找到合适的方向，但那并不是绝对的。如果你需要事务处理或是外键，那么InnoDB 可能是比较好的方式。如果你需要全文索引，那么通常来说 MyISAM是好的选择，因为这是系统内建的，然而，我们其实并不会经常地去测试两百万行记录。所以，就算是慢一点，我们可以通过使用Sphinx从InnoDB中获得全文索引。  

数据的大小，是一个影响你选择什么样存储引擎的重要因素，大尺寸的数据集趋向于选择InnoDB方式，因为其支持事务处理和故障恢复。数据库的在小决定了故障恢复的时间长短，InnoDB可以利用事务日志进行数据恢复，这会比较快。而MyISAM可能会需要几个小时甚至几天来干这些事，InnoDB只需要几分钟。  

操作数据库表的习惯可能也会是一个对性能影响很大的因素。比如： COUNT() 在 MyISAM 表中会非常快，而在InnoDB 表下可能会很痛苦。而主键查询则在InnoDB下会相当相当的快，但需要小心的是如果我们的主键太长了也会导致性能问题。大批的inserts 语句在 MyISAM下会快一些，但是updates 在InnoDB下会更快一些——尤其在并发量大的时候。  

所以，到底你检使用哪一个呢？根据经验来看，如果是一些小型的应用或项目，那么MyISAM 也许会更适合。当然，在大型的环境下使用 MyISAM 也会有很大成功的时候，但却不总是这样的。如果你正在计划使用一个超大数据量的项目，而且需要事务处理或外键支持，那么你真的应该直接使用 InnoDB方式。但需要记住InnoDB 的表需要更多的内存和存储，转换100GB 的MyISAM 表到InnoDB 表可能会让你有非常坏的体验。  

对于支持事务的InnoDB类型的表，影响速度的主要原因是AUTOCOMMIT默认设置是打开的，而且程序没有显式调用BEGIN 开始事务，导致每插入一条都自动Commit，严重影响了速度。可以在执行sql前调用begin，多条sql形成一个事务（即使autocommit打开也可以），将大大提高性能。  



InnoDB

InnoDB 给 MySQL 提供了具有事务(commit)、回滚(rollback)和崩溃修复能力 (crash recovery capabilities)的事务安全(transaction-safe (ACID compliant))型表。 InnoDB 提供了行锁(locking on row level)，提供与 Oracle 类型一致的不加锁读取(non- locking read in SELECTs)。这些特性均提高了多用户并发操作的性能表现。在InnoDB表中不需要扩大锁定 (lock escalation)，因为 InnoDB 的列锁定(row level locks)适宜非常小的空间。 InnoDB 是 MySQL 上第一个提供外键约束(FOREIGN KEY constraints)的表引擎。  

InnoDB 的设计目标是处理大容量数据库系统，它的 CPU 利用率是其它基于磁盘的关系数据库引擎所不能比的。在技术上，InnoDB 是一套放在 MySQL 后台的完整数据库系统，InnoDB 在主内存中建立其专用的缓冲池用于高速缓冲数据和索引。 InnoDB 把数据和索引存放在表空间里，可能包含多个文件，这与其它的不一样，举例来说，在 MyISAM 中，表被存放在单独的文件中。InnoDB 表的大小只受限于操作系统的文件大小，一般为 2 GB。  
InnoDB所有的表都保存在同一个数据文件 ibdata1 中（也可能是多个文件，或者是独立的表空间文件）,相对来说比较不好备份，免费的方案可以是拷贝数据文件、备份 binlog，或者用 mysqldump。  


MyISAM  
MyISAM 是MySQL缺省存贮引擎 .  
每张MyISAM 表被存放在三个文件 。frm 文件存放表格定义。 数据文件是MYD (MYData) 。 索引文件是 MYI (MYIndex) 引伸。  
因为MyISAM相对简单所以在效率上要优于InnoDB..小型应用使用MyISAM是不错的选择.  
MyISAM表是保存成文件的形式,在跨平台的数据转移中使用MyISAM存储会省去不少的麻烦  

以下是一些细节和具体实现的差别：  

1.InnoDB不支持FULLTEXT类型的索引。  
2.InnoDB 中不保存表的具体行数，也就是说，执行select count(*) from table时，InnoDB要扫描一遍整个表来计算有多少行，但是MyISAM只要简单的读出保存好的行数即可。注意的是，当count(*)语句包含 where条件时，两种表的操作是一样的。  
3.对于AUTO_INCREMENT类型的字段，InnoDB中必须包含只有该字段的索引，但是在MyISAM表中，可以和其他字段一起建立联合索引。  
4.DELETE FROM table时，InnoDB不会重新建立表，而是一行一行的删除。  
5.LOAD TABLE FROM MASTER操作对InnoDB是不起作用的，解决方法是首先把InnoDB表改成MyISAM表，导入数据后再改成InnoDB表，但是对于使用的额外的InnoDB特性（例如外键）的表不适用。  

另外，InnoDB表的行锁也不是绝对的，如果在执行一个SQL语句时MySQL不能确定要扫描的范围，InnoDB表同样会锁全表，例如 update table set num=1 where name like “%aaa%”  

任何一种表都不是万能的，只用恰当的针对业务类型来选择合适的表类型，才能最大的发挥MySQL的性能优势。  



**六、重复地总结一遍**

1、MyISAM不支持事务，InnoDB是事务类型的存储引擎，当我们的表需要用到事务支持的时候，那肯定是不能选择MyISAM了。

2、MyISAM只支持表级锁，BDB支持页级锁和表级锁默认为页级锁，而InnoDB支持行级锁和表级锁默认为行级锁

表级锁：直接锁定整张表，在锁定期间，其他进程无法对该表进行写操作，如果设置的是写锁，那么其他进程读也不允许

MyISAM是表级锁定的存储引擎，它不会出现死锁问题

对于write，表锁定原理如下：

如果表上没有锁，在其上面放置一个写锁，否则，把锁定请求放在写锁队列中。

对于read，表锁定原理如下 ：

如果表上没有写锁定，那么把一个读锁放在其上面，否则把锁请求放在读锁定队列中

当一个锁定被释放时，表可被写锁定队列中的线程得到，然后才是读锁定队列中的线程。这意味着，如果你在一个表上有许多更新，那么你的SELECT语句将等到所有的写锁定线程执行完。

行级锁：只对指定的行进行锁定，其他进程还是可以对表中的其他行进行操作的。

行级锁是Mysql粒度最小的一种锁，它能大大的减少数据库操作的冲突，但是粒度越小实现成本也越大。

行级锁可能会导致“死锁”，那到底是怎么导致的呢，分析原因：Mysql行级锁并不是直接锁记录，而是锁索引。索引分为主键索引和非主键索引两种，如果一条sql语句操作了主键索引，那么Mysql就会锁定这个主键索引，如果sql语句操作的是非主键索引，那么Mysql会先锁定这个非主键索引，再去锁定主键索引。

在UPDATE 和 DELETE操作时Mysql不仅会锁定所有WHERE 条件扫描过得索引，还会锁定相邻的键值。

“死锁”举例分析：

表Test：（ID,STATE,TIME）  主键索引：ID  非主键索引：STATE

当执行"UPDATE  STATE =1011 WHERE STATE=1000"  语句的时候会锁定STATE索引，由于STATE 是非主键索引,所以Mysql还会去请求锁定ID索引

当另一个SQL语句与语句1几乎同时执行时：“UPDATE STATE=1010 WHERE ID=1”  对于语句2 Mysql会先锁定ID索引，由于语句2操作了STATE字段，所以Mysql还会请求锁定STATE索引。这时。彼此锁定着对方需要的索引，又都在等待对方释放锁定。所以出现了"死锁"的情况。

行级锁的优点：

有许多线程访问不同的行时，只存在少量的冲突。

回滚时只有少量的更改

可以长时间锁定单一的行

行级锁缺点：

相对于页级锁和表级锁来说占用了更多的内存

当表的大部分行在使用时，比页级锁和表级锁慢，因为你必须获得更多的锁

当在大部分数据上经常使用GROUP BY操作，肯定会比表级锁和页级锁慢。

页级锁：表级锁速度快，但是冲突多；行级锁速度慢，但冲突少；页级锁就是他俩折中的，一次锁定相邻的一组记录。

3、MyISAM引擎不支持外键，InnoDB支持外键

4、MyISAM引擎的表在大量高并发的读写下会经常出现表损坏的情况

我们以前做的项目就遇到这个问题，表的INSERT 和 UPDATE操作很频繁，原来用的MyISAM引擎，导致表隔三差五就损坏，后来更换成了InnoDB引擎。

其他容易导致表损坏原因：

服务器突然断电导致数据文件损坏，强制关机（mysqld未关闭情况下）导致表损坏

mysqld进程在写入操作的时候被杀掉

磁盘故障

表损坏常见症状：

查询表不能返回数据或返回部分数据

打开表失败： Can’t open file: ‘×××.MYI’ (errno: 145) 。

Error: Table 'p' is marked as crashed and should be repaired 。

Incorrect key file for table: '...'. Try to repair it

Mysql表的恢复：

对于MyISAM表的恢复：

可以使用Mysql自带的myisamchk工具： myisamchk -r tablename  或者 myisamchk -o tablename（比前面的更保险） 对表进行修复

5、对于count()查询来说MyISAM更有优势

因为MyISAM存储了表中的行数记录，执行SELECT COUNT() 的时候可以直接获取到结果，而InnoDB需要扫描全部数据后得到结果。

但是注意一点：对于带有WHERE 条件的 SELECT COUNT()语句两种引擎的表执行过程是一样的，都需要扫描全部数据后得到结果

6、 InnoDB是为处理巨大数据量时的最大性能设计，它的CPU效率可能是任何其它基于磁盘的关系数据库引擎所不能匹敌的。

7、MyISAM支持全文索引（FULLTEXT），InnoDB不支持

8、MyISAM引擎的表的查询、更新、插入的效率要比InnoDB高

网上截取了前辈们测试结论：

测试方法：连续提交10个query， 表记录总数：38万 ， 时间单位 s

        引擎类型                    MyISAM                InnoDB              性能相差
     
        count                      0.0008357            3.0163                3609
     
        查询主键                  0.005708              0.1574                27.57
     
        查询非主键                  24.01                  80.37                3.348
     
        更新主键                  0.008124            0.8183                100.7
     
        更新非主键                0.004141            0.02625              6.338
     
        插入                        0.004188            0.3694                88.21


​    （1）加了索引以后，对于MyISAM查询可以加快：4 206.09733倍，对InnoDB查询加快510.72921倍，同时对MyISAM更新速度减慢为原来的1/2，InnoDB的更
  新速度减慢为原来的1/30。要看情况决定是否要加索引，比如不查询的log表，不要做任何的索引。

​    （2）如果你的数据量是百万级别的，并且没有任何的事务处理，那么用MyISAM是性能最好的选择。

​    （3）InnoDB表的大小更加的大，用MyISAM可省很多的硬盘空间。

​        在我们测试的这个38w的表中，表占用空间的情况如下：
​            引擎类型                    MyISAM              InnoDB
​            数据                      53,924 KB          58,976 KB
​            索引                      13,640 KB          21,072 KB
​            占用总空间              67,564 KB          80,048 KB

​        另外一个176W万记录的表， 表占用空间的情况如下：

​            引擎类型                MyIsam              InnorDB
​            数据                  56,166 KB          90,736 KB
​            索引                  67,103 KB          88,848 KB
​            占用总空间        123,269 KB        179,584 KB



七、性能对比



测试的版本是mysql  Ver 14.14 Distrib 5.1.49, for debian-linux-gnu (i686)，使用的是Innodb plugin 1.0.8（官方称比built-in版本性能更好）和默认的MyISAM。

测试机器是笔记本，配置如下：Intel 酷睿2双核 P8600，2G*2 DDR3 1066内存，320G硬盘5400转。

测试一：数据插入性能测试，这里我分别对innodb_flush_log_at_trx_commit参数打开和关闭都测了了一下，每次测试都是运行40s，表中数字都是实际插入条数。

​                       MyISAM                 Innodb (打开)      Innodb (关闭)

单线程，逐个插入         120000                 60000              60000

4线程，逐个插入          40000*4                20000*4            40000*4

单线程，批量100条/次插入  3600*100               800*100            3000*100

单线程，批量200条/次插入  1800*200               400*200            1600*200

可以发现批量插入的性能远高于单条插入，但是一次批量的大小对性能影响不大。每条记录是否都刷新日志的参数对innodb性能的影响巨大。总体上来说，MyISAM性能更优一点。这里有一点需要注意，在插入测试过程中，我对系统资源进行了监控，发现MyISAM对系统资源占用很低，但是Innodb对磁盘占用却很高，应该是对事务控制多了很多需要记录的日志。

测试二：数据读取性能测试。每次随机读取1000条记录，反复进行读取。

​                        MyISAM        Innodb

单线程，200次读取         5.7s          16.7s

4线程，200次读取          12s           40.8s

可以看出MyISAM的读取性能非常恐怖，性能差距在3倍的样子。

以上两个测试发现MyISAM在无事务的需求下几乎完胜，但是要知道它是表锁，Innodb是行锁，那么在并发读写同时存在的情况下，那结果会是怎么样呢？！

测试三：两个线程并发写入，2个线程并发读取。

​                       MyISAM                                 Innodb

逐个插入                写入40s：10000*2 读取200次*2：14s        写入40s：60000*2 读取200次*2：50s

批量100条/次插入        写入40s：1000*100*2 读取200次*2：10s      写入40s：1500*100*2 读取200次*2：50s

这下立刻显示出Innodb在并发情况下强劲的性能，几乎没有什么性能衰减。而MyISAM单条插入速度变得非常慢，批量插入也下降了40%性能。

总结一下，在写多读少的应用中还是Innodb插入性能更稳定，在并发情况下也能基本，如果是对读取速度要求比较快的应用还是选MyISAM。





## MySQL存储引擎InnoDB与Myisam的六大区别

### *分类* [编程技术](https://www.runoob.com/w3cnote_genre/code)

> 摘要: MySQL有多种存储引擎，每种存储引擎有各自的优缺点，可以择优选择使用：MyISAM、InnoDB、MERGE、MEMORY(HEAP)、BDB(BerkeleyDB)、EXAMPLE、FEDERATED、ARCHIVE、CSV、BLACKHOLE。

MySQL 有多种存储引擎，每种存储引擎有各自的优缺点，可以择优选择使用：

```
MyISAM、InnoDB、MERGE、MEMORY(HEAP)、BDB(BerkeleyDB)、EXAMPLE、FEDERATED、ARCHIVE、CSV、BLACKHOLE。
```

MySQL支持数个存储引擎作为对不同表的类型的处理器。MySQL存储引擎包括处理事务安全表的引擎和处理非事务安全表的引擎：

- MyISAM管理非事务表。它提供高速存储和检索，以及全文搜索能力。MyISAM在所有MySQL配置里被支持，它是默认的存储引擎，除非你配置MySQL默认使用另外一个引擎。

- MEMORY存储引擎提供"内存中"表。MERGE存储引擎允许集合将被处理同样的MyISAM表作为一个单独的表。就像MyISAM一样，MEMORY和MERGE存储引擎处理非事务表，这两个引擎也都被默认包含在MySQL中。

  注释：MEMORY存储引擎正式地被确定为HEAP引擎。

- InnoDB和BDB存储引擎提供事务安全表。BDB被包含在为支持它的操作系统发布的MySQL-Max二进制分发版里。InnoDB也默认被包括在所 有MySQL 5.1二进制分发版里，你可以按照喜好通过配置MySQL来允许或禁止任一引擎。

- EXAMPLE存储引擎是一个"存根"引擎，它不做什么。你可以用这个引擎创建表，但没有数据被存储于其中或从其中检索。这个引擎的目的是服务，在 MySQL源代码中的一个例子，它演示说明如何开始编写新存储引擎。同样，它的主要兴趣是对开发者。

- NDB Cluster是被MySQL Cluster用来实现分割到多台计算机上的表的存储引擎。它在MySQL-Max 5.1二进制分发版里提供。这个存储引擎当前只被Linux, Solaris, 和Mac OS X 支持。在未来的MySQL分发版中，我们想要添加其它平台对这个引擎的支持，包括Windows。

- ARCHIVE存储引擎被用来无索引地，非常小地覆盖存储的大量数据。

- CSV存储引擎把数据以逗号分隔的格式存储在文本文件中。

- BLACKHOLE存储引擎接受但不存储数据，并且检索总是返回一个空集。

- FEDERATED存储引擎把数据存在远程数据库中。在MySQL 5.1中，它只和MySQL一起工作，使用MySQL C Client API。在未来的分发版中，我们想要让它使用其它驱动器或客户端连接方法连接到另外的数据源。

### 比较常用的是 MyISAM 和 InnoBD

|                                                   | **MyISAM**                                                   | **InnoDB**                                                   |
| ------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **构成上的区别：**                                | 每个MyISAM在磁盘上存储成三个文件。第一个文件的名字以表的名字开始，扩展名指出文件类型。   .frm文件存储表定义。   数据文件的扩展名为.MYD (MYData)。   索引文件的扩展名是.MYI (MYIndex)。 | 基于磁盘的资源是InnoDB表空间数据文件和它的日志文件，InnoDB 表的大小只受限于操作系统文件的大小，一般为 2GB |
| **事务处理上方面****:**                           | MyISAM类型的表强调的是性能，其执行数度比InnoDB类型更快，但是不提供事务支持 | InnoDB提供事务支持事务，外部键（foreign key）等高级数据库功能 |
| **SELECT  UPDATE,INSERT****，****Delete****操作** | 如果执行大量的SELECT，MyISAM是更好的选择                     | **1.**如果你的数据执行大量的**INSERT****或****UPDATE**，出于性能方面的考虑，应该使用InnoDB表   **2.DELETE  FROM table**时，InnoDB不会重新建立表，而是一行一行的删除。   **3.LOAD  TABLE FROM MASTER**操作对InnoDB是不起作用的，解决方法是首先把InnoDB表改成MyISAM表，导入数据后再改成InnoDB表，但是对于使用的额外的InnoDB特性（例如外键）的表不适用 |
| **对****AUTO_INCREMENT****的操作**                | 每表一个AUTO_INCREMEN列的内部处理。   **MyISAM****为****INSERT****和****UPDATE****操作自动更新这一列**。这使得AUTO_INCREMENT列更快（至少10%）。在序列顶的值被删除之后就不能再利用。(当AUTO_INCREMENT列被定义为多列索引的最后一列，可以出现重使用从序列顶部删除的值的情况）。   AUTO_INCREMENT值可用ALTER TABLE或myisamch来重置   对于AUTO_INCREMENT类型的字段，InnoDB中必须包含只有该字段的索引，但是在MyISAM表中，可以和其他字段一起建立联合索引   更好和更快的auto_increment处理 | 如果你为一个表指定AUTO_INCREMENT列，在数据词典里的InnoDB表句柄包含一个名为自动增长计数器的计数器，它被用在为该列赋新值。   自动增长计数器仅被存储在主内存中，而不是存在磁盘上   关于该计算器的算法实现，请参考   **AUTO_INCREMENT****列在****InnoDB****里如何工作** |
| **表的具体行数**                                  | select count(*) from table,MyISAM只要简单的读出保存好的行数，注意的是，当count(*)语句包含  where条件时，两种表的操作是一样的 | InnoDB 中不保存表的具体行数，也就是说，执行select count(*) from table时，InnoDB要扫描一遍整个表来计算有多少行 |
| **锁**                                            | 表锁                                                         | 提供行锁(locking on row level)，提供与 Oracle 类型一致的不加锁读取(non-locking read in   SELECTs)，另外，InnoDB表的行锁也不是绝对的，如果在执行一个SQL语句时MySQL不能确定要扫描的范围，InnoDB表同样会锁全表， 例如update table set num=1 where name like "%aaa%" |

### MySQL 存储引擎 MyISAM 与 InnoDB 如何选择？

虽然 MySQL 里的存储引擎不只是 MyISAM 与 InnoDB 这两个，但常用的就是它俩了。可能有站长并未注意过 MySQL 的存储引擎，其实存储引擎也是数据库设计里的一大重要点，那么博客系统应该使用哪种存储引擎呢？

下面我们分别来看两种存储引擎的区别。

- 一、InnoDB支持事务，MyISAM不支持，这一点是非常之重要。事务是一种高级的处理方式，如在一些列增删改中只要哪个出错还可以回滚还原，而MyISAM就不可以了。
- 二、MyISAM适合查询以及插入为主的应用，InnoDB适合频繁修改以及涉及到安全性较高的应用
- 三、InnoDB支持外键，MyISAM不支持
- 四、MyISAM是默认引擎，InnoDB需要指定
- 五、InnoDB不支持FULLTEXT类型的索引
- 六、InnoDB中不保存表的行数，如select count(*) from table时，InnoDB需要扫描一遍整个表来计算有多少行，但是MyISAM只要简单的读出保存好的行数即可。注意的是，当count(*)语句包含where条件时MyISAM也需要扫描整个表
- 七、对于自增长的字段，InnoDB中必须包含只有该字段的索引，但是在MyISAM表中可以和其他字段一起建立联合索引
- 八、清空整个表时，InnoDB是一行一行的删除，效率非常慢。MyISAM则会重建表
- 九、InnoDB支持行锁（某些情况下还是锁整表，如 **update table set a=1 where user like '%lee%'**

通过以上九点区别，结合个人博客的特点，推荐个人博客系统使用MyISAM，因为在博客里主要操作是读取和写入，很少有链式操作。所以选择MyISAM引擎使你博客打开也页面的效率要高于InnoDB引擎的博客，当然只是个人的建议，大多数博客还是根据实际情况下谨慎选择。

**一些关于MyISAM与InnoDB选择使用：**

MYISAM和INNODB是Mysql数据库提供的两种存储引擎。两者的优劣可谓是各有千秋。INNODB会支持一些关系数据库的高级功能，如事务功能和行级锁，MYISAM不支持。MYISAM的性能更优，占用的存储空间少。所以，选择何种存储引擎，视具体应用而定。

如果你的应用程序一定要使用事务，毫无疑问你要选择INNODB引擎。但要注意，INNODB的行级锁是有条件的。在where条件没有使用主键时，照样会锁全表。比如DELETE FROM mytable这样的删除语句。

如果你的应用程序对查询性能要求较高，就要使用MYISAM了。MYISAM索引和数据是分开的，而且其索引是压缩的，可以更好地利用内存。所以它的查询性能明显优于INNODB。压缩后的索引也能节约一些磁盘空间。MYISAM拥有全文索引的功能，这可以极大地优化LIKE查询的效率。

有人说MYISAM只能用于小型应用，其实这只是一种偏见。如果数据量比较大，这是需要通过升级架构来解决，比如分表分库，而不是单纯地依赖存储引擎。

**其他一些说法：**

现在一般都是选用innodb了，主要是myisam的全表锁，读写串行问题，并发效率锁表，效率低myisam对于读写密集型应用一般是不会去选用的。

关于Mysql数据库默认的存储引擎：

MyISAM和InnoDB是MySQL的两种存储引擎。如果是默认安装，那就应该是InnoDB，你可以在my.ini文件中找到default-storage-engine=INNODB；当然你可以在建表时指定相应的存储引擎。通过show create table xx 可以看见相应信息。

### Mysql中InnoDB和MyISAM的比较

**MyISAM：**

每个MyISAM在磁盘上存储成三个文件。第一个文件的名字以表的名字开始，扩展名指出文件类型。.frm文件存储表定义。数据文件的扩展名为.MYD (MYData)。

MyISAM表格可以被压缩，而且它们支持全文搜索。不支持事务，而且也不支持外键。如果事物回滚将造成不完全回滚，不具有原子性。在进行updata时进行表锁，并发量相对较小。如果执行大量的SELECT，MyISAM是更好的选择。

MyISAM的索引和数据是分开的，并且索引是有压缩的，内存使用率就对应提高了不少。能加载更多索引，而Innodb是索引和数据是紧密捆绑的，没有使用压缩从而会造成Innodb比MyISAM体积庞大不小

MyISAM缓存在内存的是索引，不是数据。而InnoDB缓存在内存的是数据，相对来说，服务器内存越大，InnoDB发挥的优势越大。

**优点：**查询数据相对较快，适合大量的select，可以全文索引。

**缺点：**不支持事务，不支持外键，并发量较小，不适合大量update

**InnoDB：**

这种类型是事务安全的。.它与BDB类型具有相同的特性,它们还支持外键。InnoDB表格速度很快。具有比BDB还丰富的特性,因此如果需要一个事务安全的存储引擎，建议使用它。在update时表进行行锁，并发量相对较大。如果你的数据执行大量的INSERT或UPDATE，出于性能方面的考虑，应该使用InnoDB表。

**优点：**支持事务，支持外键，并发量较大，适合大量update

**缺点：**查询数据相对较快，不适合大量的select

对于支持事物的InnoDB类型的表，影响速度的主要原因是AUTOCOMMIT默认设置是打开的，而且程序没有显式调用BEGIN 开始事务，导致每插入一条都自动Commit，严重影响了速度。可以在执行sql前调用begin，多条sql形成一个事物（即使autocommit打开也可以），将大大提高性能。

**基本的差别为**：MyISAM类型不支持事务处理等高级处理，而InnoDB类型支持。

MyISAM类型的表强调的是性能，其执行数度比InnoDB类型更快，但是不提供事务支持，而InnoDB提供事务支持已经外部键等高级数据库功能。

**其他比较：**

MyIASM是IASM表的新版本，有如下扩展：

- 二进制层次的可移植性。
- NULL列索引。
- 对变长行比ISAM表有更少的碎片。
- 支持大文件。
- 更好的索引压缩。
- 更好的键吗统计分布。
- 更好和更快的auto_increment处理。

**以下是一些细节和具体实现的差别：**

- 1.InnoDB不支持FULLTEXT类型的索引。
- 2.InnoDB 中不保存表的具体行数，也就是说，执行select count(*) from table时，InnoDB要扫描一遍整个表来计算有多少行，但是MyISAM只要简单的读出保存好的行数 即可。注意的是，当count(*)语句包含 where条件时，两种表的操作是一样的。
- 3.对于AUTO_INCREMENT类型的字段，InnoDB中必须包含只有该字段的索引，但是在MyISAM表中，可以和其他字段一起建立联合索引。
- 4.DELETE FROM table时，InnoDB不会重新建立表，而是一行一行的删除。
- 5.LOAD TABLE FROM MASTER操作对InnoDB是不起作用的，解决方法是首先把InnoDB表改成MyISAM表，导入数据后再改成InnoDB表，但是对于使用的额外的 InnoDB特性（例如外键）的表不适用。

另外，InnoDB表的行锁也不是绝对的，如果在执行一个SQL语句时MySQL不能确定要扫描的范围，InnoDB表同样会锁全表，例如update table set num=1 where name like "%aaa%"

任何一种表都不是万能的，只用恰当的针对业务类型来选择合适的表类型，才能最大的发挥MySQL的性能优势。

**innodb和myisam更新比较：**

innodb的数据组织就是按照主键建成的一个B+树，如果没有显示的定义主键，那么innodb会选区一个not null unique key，作为主键，如果还是没有，那么innodb会创建一个 6字节的主键，主键索引到页不是具体的行位置

不是递增的主键会使得插入的速度很慢，例如使用手机号或身份证号做为主键，所以善用AUTO_INCREMENT

表大不可怕，可怕的是count或者高偏移limit,可以将大的limit big换成 limit max_id, xxxxx

```
Limit 0 1000 | limit 1001 1000 | limit 2001 1000

Limit 0 1000 | where id>max_id1 limit 1000 | where id>max_id2 limit 1000
```

对于InnoDB来说，按照某列分表，想在单台服务器上提高性能是没有意义的

插入的速度和查询的速度有时候是不可调和的矛盾

说InnoDB不适合做count是不对的，MyISAM也是一样的慢，只不过MyISAM将正表的行数缓存起来，所以count整表很快，如果有查询条件，并且不是主键查询，那就没有什么区别，主键count慢的原因是innodb是按照主键组织的，按照主键count的时候，会加载数据

InnoDB的页式存储会使得InnoDB更容易做整表缓存和热备份

如果表索引很多，那么InnoDB的更新速度要大于MyISAM，因为InnoDB的辅助索引关联的是表的主键，是一个逻辑的值，而MyISAM的所有索引关联的是数据的物理位置，更新时有可能数据的物理位置发生变化，如果发生变化，那么所有的索引都要做更新

InnoDB 中不保存表的具体行数，也就是说，执行select count(*) from table时，InnoDB要扫描一遍整个表来计算有多少行，但是MyISAM只要简单的读出保存好的行数即可。注意的是，当count(*)语句包含 where条件时，两种表的操作是一样的。





### 什么是MyISAM 和InnoDB

> MyISAM是MySQL的默认数据库引擎（5.5版之前），由早期的ISAM所改良。虽然性能极佳，但却有一个缺点：不支持事务处理（transaction）。
>
> InnoDB，是MySQL的数据库引擎之一，为MySQL AB发行binary的标准之一。InnoDB由Innobase Oy公司所开发，2006年五月时由甲骨文公司并购。与传统的ISAM与MyISAM相比，InnoDB的最大特色就是支持了ACID兼容的事务（Transaction）功能，类似于PostgreSQL。

MyISAM：它是基于传统的ISAM类型，ISAM是Indexed Sequential Access Method (有索引的顺序访问方法) 的缩写，它是存储记录和文件的标准方法。不是事务安全的，而且不支持外键，如果执行大量的select，insert MyISAM比较适合。

InnoDB：支持事务安全的引擎，支持外键、行锁、事务是他的最大特点。如果有大量的update和insert，建议使用InnoDB，特别是针对多个并发和QPS较高的情况。

### MyISAM与InnoDB的主要区别:

1. 存储结构

   MyISAM：每个MyISAM在磁盘上存储成三个文件。1）.frm 用于存储表的定义。2）.MYD 用于存放数据。 3）.MYI 用于存放表索引

   InnoDB：所有的表都保存在同一个数据文件中（也可能是多个文件，或者是独立的表空间文件），InnoDB表的大小只受限于操作系统文件的大小，一般为2GB。

2. 存储空间

   MyISAM：可被压缩，存储空间较小。支持三种不同的存储格式：静态表(默认，但是注意数据末尾不能有空格，会被去掉)、动态表、压缩表。

   InnoDB：需要更多的内存和存储，它会在主内存中建立其专用的缓冲池用于高速缓冲数据和索引。

3. 可移植性、备份及恢复

   MyISAM：数据是以文件的形式存储，所以在跨平台的数据转移中会很方便。在备份和恢复时可单独针对某个表进行操作。

   InnoDB：免费的方案可以是拷贝数据文件、备份 binlog，或者用 mysqldump，在数据量达到几十G的时候就相对痛苦了。

4. 事务支持

   MyISAM：强调的是性能，每次查询具有原子性,其执行数度比InnoDB类型更快，但是不提供事务支持。
    InnoDB：提供事务支持事务，外部键等高级数据库功能。 具有事务(commit)、回滚(rollback)和崩溃修复能力(crash recovery capabilities)的事务安全(transaction-safe (ACID compliant))型表。

5. AUTO_INCREMENT

   MyISAM：可以和其他字段一起建立联合索引。引擎的自动增长列必须是索引，如果是组合索引，自动增长可以不是第一列，他可以根据前面几列进行排序后递增。
    InnoDB：InnoDB中必须包含只有该字段的索引。引擎的自动增长列必须是索引，如果是组合索引也必须是组合索引的第一列。

6. 表锁差异

   MyISAM：只支持表级锁，用户在操作myisam表时，select，update，delete，insert语句都会给表自动加锁，如果加锁以后的表满足insert并发的情况下，可以在表的尾部插入新的数据。

   InnoDB：

   1. 支持事务和行级锁，是innodb的最大特色。行锁大幅度提高了多用户并发操作的新能。但是InnoDB的行锁，只是在WHERE的主键是有效的，非主键的WHERE都会锁全表的。
   2. 事务的ACID属性：atomicity,consistent,isolation,durable。
   3. 并发事务带来的几个问题：更新丢失，脏读，不可重复读，幻读。
   4. 事务隔离级别：未提交读(Read uncommitted)，已提交读(Read committed)，可重复读(Repeatable read)，可序列化(Serializable)

   | 读数据一致性及并发副作用   |          读数据一致性          | 脏读 | 不可重复读 | 幻读 |
   | :------------------------- | :----------------------------: | ---: | ---------: | ---: |
   | 为提交读(read uncommitted) | 最低级别，不读物理上顺坏的数据 |   是 |         是 |   是 |
   | 已提交读(read committed)   |             语句级             |   否 |         是 |   是 |
   | 可重复读(Repeatable red)   |             事务级             |   否 |         否 |   是 |
   | 可序列化(Serializable)     |        最高级别，事务级        |   否 |         否 |   否 |

1. 全文索引

   MyISAM：支持 FULLTEXT类型的全文索引
    InnoDB：不支持FULLTEXT类型的全文索引，但是innodb可以使用sphinx插件支持全文索引，并且效果更好。

2. 表主键

   MyISAM：允许没有任何索引和主键的表存在，索引都是保存行的地址。
    InnoDB：如果没有设定主键或者非空唯一索引，就会自动生成一个6字节的主键(用户不可见)，数据是主索引的一部分，附加索引保存的是主索引的值。

3. 表的具体行数

   MyISAM：保存有表的总行数，如果select count( * ) from table;会直接取出出该值。
    InnoDB：没有保存表的总行数，如果使用select count( * ) from table；就会遍历整个表，消耗相当大，但是在加了wehre条件后，myisam和innodb处理的方式都一样。

4. CURD操作

   MyISAM：如果执行大量的SELECT，MyISAM是更好的选择。
    InnoDB：如果你的数据执行大量的INSERT或UPDATE，出于性能方面的考虑，应该使用InnoDB表。DELETE 从性能上InnoDB更优，但DELETE FROM table时，InnoDB不会重新建立表，而是一行一行的删除，在innodb上如果要清空保存有大量数据的表，最好使用truncate table这个命令。

5. 外键

   MyISAM：不支持
    InnoDB：支持
    通过上述的分析，基本上可以考虑使用InnoDB来替代MyISAM引擎了，原因是InnoDB自身很多良好的特点，比如事务支持、存储 过程、视图、行级锁定等等，在并发很多的情况下，相信InnoDB的表现肯定要比MyISAM强很多。另外，任何一种表都不是万能的，只用恰当的针对业务类型来选择合适的表类型，才能最大的发挥MySQL的性能优势。如果不是很复杂的Web应用，非关键应用，还是可以继续考虑MyISAM的，这个具体情况可以自己斟酌。

### 应用场景：

1. MyISAM管理非事务表。它提供高速存储和检索，以及全文搜索能力。如果应用中需要执行大量的SELECT查询，那么MyISAM是更好的选择。
2. InnoDB用于事务处理应用程序，具有众多特性，包括ACID事务支持。如果应用中需要执行大量的INSERT或UPDATE操作，则应该使用InnoDB，这样可以提高多用户并发操作的性能。

### 开发的注意事项

1. 可以用 show create table tablename 命令看表的引擎类型。
2. 对不支持事务的表做start/commit操作没有任何效果，在执行commit前已经提交。
3. 可以执行以下命令来切换非事务表到事务（数据不会丢失），innodb表比myisam表更安全：alter table tablename type=innodb;或者使用 alter table tablename engine = innodb;
4. 默认innodb是开启自动提交的，如果你按照myisam的使用方法来编写代码页不会存在错误，只是性能会很低。如何在编写代码时候提高数据库性能呢？
5. 尽量将多个语句绑到一个事务中，进行提交，避免多次提交导致的数据库开销。
6. 在一个事务获得排他锁或者意向排他锁以后，如果后面还有需要处理的sql语句，在这两条或者多条sql语句之间程序应尽量少的进行逻辑运算和处理，减少锁的时间。
7. 尽量避免死锁
8. sql语句如果有where子句一定要使用索引，尽量避免获取意向排他锁。
9. 针对我们自己的数据库环境，日志系统是直插入，不修改的，所以我们使用混合引擎方式，ZION_LOG_DB照旧使用myisam存储引擎，只有ZION_GAME_DB，ZION_LOGIN_DB，DAUM_BILLING使用Innodb引擎。

### 总结

在大数据量，高并发量的互联网业务场景下，对于MyISAM和InnoDB

有where条件，count(*)两个存储引擎性能差不多
 不要使用全文索引，应当使用《索引外置》的设计方案
 事务影响性能，强一致性要求才使用事务
 不用外键，由应用程序来保证完整性
 不命中索引，InnoDB也不能用行锁

### 结论

在大数据量，高并发量的互联网业务场景下，请使用InnoDB:

行锁，对提高并发帮助很大
 事务，对数据一致性帮助很大
 这两个点，是InnoDB最吸引人的地方。


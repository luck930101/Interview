**简介：** MySQL的事务隔离级别一共有四个，分别是读未提交、读已提交、可重复读以及可串行化。

## 事前准备数据

```
mysql> create table city(
    -> id int(10) auto_increment,
    -> name varchar(30),
    -> primary key (id)
    -> )engine=innodb charset=utf8mb4;

insert into city(name) values('武汉市');

mysql> select * from city;
+----+-----------+
| id | name |
+----+-----------+
| 1 | 武汉市 |
+----+-----------+
```

## 事务并发可能出现的情况

#### 脏读（Dirty Read）

> 一个事务读到了另一个未提交事务修改过的数据

![从根上理解MySQL事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/04/32495/Wcv8DTijTL.png!large)

> 会话B开启一个事务，把id=1的name为武汉市修改成温州市，此时另外一个会话A也开启一个事务，读取id=1的name，此时的查询结果为温州市，会话B的事务最后回滚了刚才修改的记录，这样会话A读到的数据是不存在的，这个现象就是脏读。（脏读只在读未提交隔离级别才会出现）

#### 不可重复读（Non-Repeatable Read）

> 一个事务只能读到另一个已经提交的事务修改过的数据，并且其他事务每对该数据进行一次修改并提交后，该事务都能查询得到最新值。（不可重复读在读未提交和读已提交隔离级别都可能会出现）

![从根上理解 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/YdNemia6wc.png!large)

> 会话A开启一个事务，查询id=1的结果，此时查询的结果name为武汉市。接着会话B把id=1的name修改为温州市（隐式事务，因为此时的autocommit为1，每条SQL语句执行完自动提交），此时会话A的事务再一次查询id=1的结果，读取的结果name为温州市。会话B再此修改id=1的name为杭州市，会话A的事务再次查询id=1，结果name的值为杭州市，这种现象就是不可重复读。

#### 幻读（Phantom）

> 一个事务先根据某些条件查询出一些记录，之后另一个事务又向表中插入了符合这些条件的记录，原先的事务再次按照该条件查询时，能把另一个事务插入的记录也读出来。（幻读在读未提交、读已提交、可重复读隔离级别都可能会出现）

![从根上理解 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/04/32495/0sCtxw1Jno.png!large)

> 会话A开启一个事务，查询id>0的记录，此时会查到name=武汉市的记录。接着会话B插入一条name=温州市的数据（隐式事务，因为此时的autocommit为1，每条SQL语句执行完自动提交），这时会话A的事务再以刚才的查询条件（id>0）再一次查询，此时会出现两条记录（name为武汉市和温州市的记录），这种现象就是幻读。

## 事务的隔离级别

> MySQL的事务隔离级别一共有四个，分别是读未提交、读已提交、可重复读以及可串行化。
>
> MySQL的隔离级别的作用就是让事务之间互相隔离，互不影响，这样可以保证事务的一致性。
>
> 隔离级别比较：可串行化>可重复读>读已提交>读未提交
>
> 隔离级别对性能的影响比较：可串行化>可重复读>读已提交>读未提交
>
> 由此看出，隔离级别越高，所需要消耗的MySQL性能越大（如事务并发严重性），为了平衡二者，一般建议设置的隔离级别为可重复读，MySQL默认的隔离级别也是可重复读。

#### 读未提交（READ UNCOMMITTED）

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/iL6jfZxiHJ.png!large)

> 在读未提交隔离级别下，事务A可以读取到事务B修改过但未提交的数据。
>
> 可能发生脏读、不可重复读和幻读问题，一般很少使用此隔离级别。

#### 读已提交（READ COMMITTED）

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/BsMcuysaIB.png!large)

> 在读已提交隔离级别下，事务B只能在事务A修改过并且已提交后才能读取到事务B修改的数据。
>
> 读已提交隔离级别解决了脏读的问题，但可能发生不可重复读和幻读问题，一般很少使用此隔离级别。

#### 可重复读（REPEATABLE READ）

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/yjRtVOpMBZ.png!large)

> 在可重复读隔离级别下，事务B只能在事务A修改过数据并提交后，自己也提交事务后，才能读取到事务B修改的数据。
>
> 可重复读隔离级别解决了脏读和不可重复读的问题，但可能发生幻读问题。
>
> 提问：为什么上了写锁（写操作），别的事务还可以读操作？
>
> 因为InnoDB有MVCC机制（多版本并发控制），可以使用快照读，而不会被阻塞。

#### 可串行化（SERIALIZABLE）

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/S0Y1nk8yv6.png!large)

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/LIfaeTxwPL.png!large)

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/q4vVuHzqO0.png!large)

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/l1BwLlDlYp.png!large)

> 各种问题（脏读、不可重复读、幻读）都不会发生，通过加锁实现（读锁和写锁）。

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/9Lpt4gaGNi.png!large)

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/2yNLgxMBp9.png!large)

## 隔离级别的实现原理

> 使用MySQL的默认隔离级别（可重复读）来进行说明。
>
> 每条记录在更新的时候都会同时记录一条回滚操作（回滚操作日志undo log）。同一条记录在系统中可以存在多个版本，这就是数据库的多版本并发控制（MVCC）。即通过回滚（rollback操作），可以回到前一个状态的值。
>
> 假设一个值从 1 被按顺序改成了 2、3、4，在回滚日志里面就会有类似下面的记录。

![彻底搞懂 MySQL 事务的隔离级别](https://cdn.learnku.com/uploads/images/202002/05/32495/mfZfSEBBSn.png!large)

> 当前值是 4，但是在查询这条记录的时候，不同时刻启动的事务会有不同的 read-view。如图中看到的，在视图 A、B、C 里面，这一个记录的值分别是 1、2、4，同一条记录在系统中可以存在多个版本，就是数据库的多版本并发控制（MVCC）。对于 read-view A，要得到 1，就必须将当前值依次执行图中所有的回滚操作得到。
>
> 同时你会发现，即使现在有另外一个事务正在将 4 改成 5，这个事务跟 read-view A、B、C 对应的事务是不会冲突的。
>
> 提问：回滚操作日志（undo log）什么时候删除？
>
> MySQL会判断当没有事务需要用到这些回滚日志的时候，回滚日志会被删除。
>
> 提问：什么时候不需要了？
>
> 当系统里么有比这个回滚日志更早的read-view的时候。

## 查看当前会话隔离级别

#### 方式1

```
命令：SHOW VARIABLES LIKE 'transaction_isolation';

mysql> show variables like 'transaction_isolation';
+-----------------------+--------------+
| Variable_name  | Value |
+-----------------------+--------------+
| transaction_isolation | SERIALIZABLE |
+-----------------------+--------------+
```

#### 方式2

```
命令：SELECT @@transaction_isolation;

mysql> select @@transaction_isolation;
+-------------------------+
| @@transaction_isolation |
+-------------------------+
| SERIALIZABLE            |
+-------------------------+
```

## 设置隔离级别

#### 方式1：通过set命令

```
SET [GLOBAL|SESSION] TRANSACTION ISOLATION LEVEL level;
其中level有4种值：
level: {
     REPEATABLE READ
   | READ COMMITTED
   | READ UNCOMMITTED
   | SERIALIZABLE
}
```

##### 关键词：GLOBAL

```
SET GLOBAL TRANSACTION ISOLATION LEVEL level;
* 只对执行完该语句之后产生的会话起作用
* 当前已经存在的会话无效
```

##### 关键词：SESSION

```
SET SESSION TRANSACTION ISOLATION LEVEL level;
* 对当前会话的所有后续的事务有效
* 该语句可以在已经开启的事务中间执行，但不会影响当前正在执行的事务
* 如果在事务之间执行，则对后续的事务有效。
```

##### 无关键词

```
SET TRANSACTION ISOLATION LEVEL level;
* 只对当前会话中下一个即将开启的事务有效
* 下一个事务执行完后，后续事务将恢复到之前的隔离级别
* 该语句不能在已经开启的事务中间执行，会报错的
```

#### 方式2：通过服务启动项命令

> 可以修改启动参数transaction-isolation的值
>
> 比方说我们在启动服务器时指定了--transaction-isolation=READ UNCOMMITTED，那么事务的默认隔离级别就从原来的REPEATABLE READ变成了READ UNCOMMITTED。

SQL 关系型数据库 MySQL 数据库
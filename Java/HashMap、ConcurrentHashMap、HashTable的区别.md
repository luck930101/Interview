## HashMap vs ConcurrentHashMap

引入`ConcurrentHashMap`是为了在同步集合HashTable之间有更好的选择，`HashTable`与`HashMap`、`ConcurrentHashMap`主要的区别在于HashMap不是同步的、线程不安全的和不适合应用于多线程并发环境下，而`ConcurrentHashMap`是线程安全的集合容器，特别是在多线程和并发环境中，通常作为`Map`的主要实现。除了线程安全外，他们之间还有一些细微的不同，本文会介绍到。顺便说说，`HashMap`和`ConcurrentHashMap`还有`ConcurrentHashMap`和`Hashtable`两者之间的区别在Java面试中经常出现，特别是高级Java程序员。

## HashMap与ConcurrentHashMap的区别

在这部分，我们会看到更多关于`HashMap`和`ConcurrentHashMap`的细节和对比它们之间的参数比如线程安全、同步、性能和基本的使用。

1. 就像上面所说他们之间的第一个重要的区别就是`ConcurrentHashMap`是线程安全的和在并发环境下不需要加额外的同步。虽然它不像`Hashtable`那样需要同样的同步等级(全表锁)，但也有很多实际的用途。
2. 你可以使用`Collections.synchronizedMap(HashMap)`来包装HashMap作为同步容器，这时它的作用几乎与`Hashtable`一样,当每次对`Map`做修改操作的时候都会锁住这个`Map`对象，而`ConcurrentHashMap`会基于并发的等级来划分整个Map来达到线程安全，它只会锁操作的那一段数据而不是整个`Map`都上锁。
3.  `ConcurrentHashMap`有很好的扩展性，在多线程环境下性能方面比做了同步的`HashMap`要好，但是在单线程环境下，`HashMap`会比`ConcurrentHashMap`好一点。

总结一下以上两者的区别，它们在线程安全、扩展性、同步之间的区别。如果是用于缓存的话，`ConcurrentHashMap`是一个更好的选择，在Java应用中会经常用到。`ConcurrentHashMap`在读操作线程数多于写操作线程数的情况下更胜一筹。

## ConcurrentHashMap vs Hashtable vs Synchronized Map

虽然三个集合类在多线程并发应用中都是线程安全的，但是他们有一个重大的差别，就是他们各自实现线程安全的方式。`Hashtable`是jdk1的一个遗弃的类，它把所有方法都加上`synchronized`关键字来实现线程安全。所有的方法都同步这样造成多个线程访问效率特别低。`Synchronized Map`与`HashTable`差别不大，也是在并发中作类似的操作，两者的唯一区别就是`Synchronized Map`没被遗弃，它可以通过使用`Collections.synchronizedMap()`来包装`Map`作为同步容器使用。

另一方面，`ConcurrentHashMap`的设计有点特别，表现在多个线程操作上。它不用做外的同步的情况下默认同时允许16个线程读和写这个Map容器。因为其内部的实现剥夺了锁，使它有很好的扩展性。不像`HashTable`和`Synchronized Map`，`ConcurrentHashMap`不需要锁整个Map，相反它划分了多个段(segments)，要操作哪一段才上锁那段数据。

坦白说，集合类是一个最重要的Java API，我觉得恰当的使用它们是一种艺术。依我个人经验，我会使用`ArrayList`这些容器来提高自己的Java程序的性能，而不会去用一些遗弃的容器比如`Vector`等等，在Java 5之前，Java集合容器有一个很致命的缺陷就是缺乏可扩展性。
 同步集合类比如`Hashtable`和`Vector`在多线程Java应用里面逐渐成为障碍物；在jdk5后出现一些很好的并发集合，对大容量、低延迟的电子交易系统有很大影响，是快速存取数据的支柱。
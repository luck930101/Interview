了解ConcurrentHashMap 实现原理，建议首先了解下[HashMap](https://link.jianshu.com?t=(http%3A%2F%2Fwww.jianshu.com%2Fp%2Fb2d611c01bf3))实现原理。
 [HashMap 源码解析(JDK1.8)](https://www.jianshu.com/p/b2d611c01bf3)

## 为什么要用ConcurrentHashMap

HashMap线程不安全，而Hashtable是线程安全，但是它使用了synchronized进行方法同步，插入、读取数据都使用了synchronized，当插入数据的时候不能进行读取（相当于把整个Hashtable都锁住了，全表锁），当多线程并发的情况下，都要竞争同一把锁，导致效率极其低下。而在JDK1.5后为了改进Hashtable的痛点，ConcurrentHashMap应运而生。

## ConcurrentHashMap为什么高效？

#### JDK1.5中的实现

ConcurrentHashMap使用的是分段锁技术,将ConcurrentHashMap将锁一段一段的存储，然后给每一段数据配一把锁（segment），当一个线程占用一把锁（segment）访问其中一段数据的时候，其他段的数据也能被其它的线程访问，默认分配16个segment。默认比Hashtable效率提高16倍。

ConcurrentHashMap的结构图如下（网友贡献的图，哈）：





![img](https:////upload-images.jianshu.io/upload_images/2843224-25151c12024f0bfb.png?imageMogr2/auto-orient/strip|imageView2/2/w/555/format/webp)

Paste_Image.png

#### JDK1.8中的实现

ConcurrentHashMap取消了segment分段锁，而采用CAS和synchronized来保证并发安全。数据结构跟HashMap1.8的结构一样，**数组+链表/红黑二叉树**。
 synchronized只锁定当前链表或红黑二叉树的首节点，这样只要hash不冲突，就不会产生并发，效率又提升N倍。

JDK1.8的ConcurrentHashMap的结构图如下：



![img](https:////upload-images.jianshu.io/upload_images/2843224-59ca97f3ae25b043.png?imageMogr2/auto-orient/strip|imageView2/2/w/681/format/webp)

Paste_Image.png

> **TreeBin:** 红黑二叉树节点
>  **Node:** 链表节点

## ConcurrentHashMap 源码分析

ConcurrentHashMap 类结构参照[HashMap](https://link.jianshu.com?t=(http%3A%2F%2Fwww.jianshu.com%2Fp%2Fb2d611c01bf3))，这里列出HashMap没有的几个属性。



```java
/**
     * Table initialization and resizing control.  When negative, the
     * table is being initialized or resized: -1 for initialization,
     * else -(1 + the number of active resizing threads).  Otherwise,
     * when table is null, holds the initial table size to use upon
     * creation, or 0 for default. After initialization, holds the
     * next element count value upon which to resize the table.
     hash表初始化或扩容时的一个控制位标识量。
     负数代表正在进行初始化或扩容操作
     -1代表正在初始化
     -N 表示有N-1个线程正在进行扩容操作
     正数或0代表hash表还没有被初始化，这个数值表示初始化或下一次进行扩容的大小
     */
    private transient volatile int sizeCtl; 
    // 以下两个是用来控制扩容的时候 单线程进入的变量
    /**
     * The number of bits used for generation stamp in sizeCtl.
     * Must be at least 6 for 32bit arrays.
     */
    private static int RESIZE_STAMP_BITS = 16;
    /**
     * The bit shift for recording size stamp in sizeCtl.
     */
    private static final int RESIZE_STAMP_SHIFT = 32 - RESIZE_STAMP_BITS;
    
    
    /*
     * Encodings for Node hash fields. See above for explanation.
     */
    static final int MOVED     = -1; // hash值是-1，表示这是一个forwardNode节点
    static final int TREEBIN   = -2; // hash值是-2  表示这时一个TreeBin节点
```

**分析代码主要目的：分析是如果利用CAS和Synchronized进行高效的同步更新数据。**
 下面插入数据源码：



```java
public V put(K key, V value) {
    return putVal(key, value, false);
}

    /** Implementation for put and putIfAbsent */
final V putVal(K key, V value, boolean onlyIfAbsent) {
    //ConcurrentHashMap 不允许插入null键，HashMap允许插入一个null键
    if (key == null || value == null) throw new NullPointerException();
    //计算key的hash值
    int hash = spread(key.hashCode());
    int binCount = 0;
    //for循环的作用：因为更新元素是使用CAS机制更新，需要不断的失败重试，直到成功为止。
    for (Node<K,V>[] tab = table;;) {
        // f：链表或红黑二叉树头结点，向链表中添加元素时，需要synchronized获取f的锁。
        Node<K,V> f; int n, i, fh;
        //判断Node[]数组是否初始化，没有则进行初始化操作
        if (tab == null || (n = tab.length) == 0)
            tab = initTable();
        //通过hash定位Node[]数组的索引坐标，是否有Node节点，如果没有则使用CAS进行添加（链表的头结点），添加失败则进入下次循环。
        else if ((f = tabAt(tab, i = (n - 1) & hash)) == null) {
            if (casTabAt(tab, i, null,
                         new Node<K,V>(hash, key, value, null)))
                break;                   // no lock when adding to empty bin
        }
        //检查到内部正在移动元素（Node[] 数组扩容）
        else if ((fh = f.hash) == MOVED)
            //帮助它扩容
            tab = helpTransfer(tab, f);
        else {
            V oldVal = null;
            //锁住链表或红黑二叉树的头结点
            synchronized (f) {
                //判断f是否是链表的头结点
                if (tabAt(tab, i) == f) {
                    //如果fh>=0 是链表节点
                    if (fh >= 0) {
                        binCount = 1;
                        //遍历链表所有节点
                        for (Node<K,V> e = f;; ++binCount) {
                            K ek;
                            //如果节点存在，则更新value
                            if (e.hash == hash &&
                                ((ek = e.key) == key ||
                                 (ek != null && key.equals(ek)))) {
                                oldVal = e.val;
                                if (!onlyIfAbsent)
                                    e.val = value;
                                break;
                            }
                            //不存在则在链表尾部添加新节点。
                            Node<K,V> pred = e;
                            if ((e = e.next) == null) {
                                pred.next = new Node<K,V>(hash, key,
                                                          value, null);
                                break;
                            }
                        }
                    }
                    //TreeBin是红黑二叉树节点
                    else if (f instanceof TreeBin) {
                        Node<K,V> p;
                        binCount = 2;
                        //添加树节点
                        if ((p = ((TreeBin<K,V>)f).putTreeVal(hash, key,
                                                      value)) != null) {
                            oldVal = p.val;
                            if (!onlyIfAbsent)
                                p.val = value;
                        }
                    }
                }
            }
            
            if (binCount != 0) {
                //如果链表长度已经达到临界值8 就需要把链表转换为树结构
                if (binCount >= TREEIFY_THRESHOLD)
                    treeifyBin(tab, i);
                if (oldVal != null)
                    return oldVal;
                break;
            }
        }
    }
    //将当前ConcurrentHashMap的size数量+1
    addCount(1L, binCount);
    return null;
}
```

1. 判断Node[]数组是否初始化，没有则进行初始化操作
2. 通过hash定位Node[]数组的索引坐标，是否有Node节点，如果没有则使用CAS进行添加（链表的头结点），添加失败则进入下次循环。
3. 检查到内部正在扩容，如果正在扩容，就帮助它一块扩容。
4. 如果f!=null，则使用synchronized锁住f元素（链表/红黑二叉树的头元素）
    4.1 如果是Node(链表结构)则执行链表的添加操作。
    4.2 如果是TreeNode(树型结果)则执行树添加操作。
5. 判断链表长度已经达到临界值8 就需要把链表转换为树结构。

总结：
     JDK8中的实现也是锁分离的思想，它把锁分的比segment（JDK1.5）更细一些，只要hash不冲突，就不会出现并发获得锁的情况。它首先使用无锁操作CAS插入头结点，如果插入失败，说明已经有别的线程插入头结点了，再次循环进行操作。如果头结点已经存在，则通过synchronized获得头结点锁，进行后续的操作。性能比segment分段锁又再次提升。
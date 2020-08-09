Java为数据结构中的映射定义了一个接口java.util.Map，它有四个实现类，分别是HashMap、HashTable、LinkedHashMap和TreeMap。本节实例主要介绍这4中实例的用法和区别

## 关键技术剖析：

Map用于存储键值对，根据键得到值，因此不允许键重复，值可以重复。
（1）HashMap是一个最常用的Map，它根据键的hashCode值存储数据，根据键可以直接获取它的值，具有很快的访问速度。HashMap最多只允许一条记录的键为null，不允许多条记录的值为null。HashMap不支持线程的同步，即任一时刻可以有多个线程同时写HashMap，可能会导致数据的不一致。如果需要同步，可以用Collections.synchronizedMap(HashMap map)方法使HashMap具有同步的能力。
（2）Hashtable与HashMap类似，不同的是：它不允许记录的键或者值为空；它支持线程的同步，即任一时刻只有一个线程能写Hashtable，然而，这也导致了Hashtable在写入时会比较慢。
（3）LinkedHashMap保存了记录的插入顺序，在用Iteraor遍历LinkedHashMap时，先得到的记录肯定是先插入的。在遍历的时候会比HashMap慢。有HashMap的全部特性。
（4）TreeMap能够把它保存的记录根据键排序，默认是按升序排序，也可以指定排序的比较器。当用Iteraor遍历TreeMap时，得到的记录是排过序的。TreeMap的键和值都不能为空。

### 使用情况

一般情况下，我们用的最多的是HashMap,HashMap里面存入的键值对在取出的时候是随机的,它根据键的HashCode值存储数据,根据键可以直接获取它的值，具有很快的访问速度。
在Map 中插入、删除和定位元素，HashMap 是最好的选择。
TreeMap取出来的是排序后的键值对。但如果您要按自然顺序或自定义顺序遍历键，那么TreeMap会更好。
LinkedHashMap 是HashMap的一个子类，如果需要输出的顺序和输入的相同,那么用LinkedHashMap可以实现,它还可以按读取顺序来排列，像连接池中可以应用。

1. HashSet是通过HashMap实现的,TreeSet是通过TreeMap实现的,只不过Set用的只是Map的key
2. Map的key和Set都有一个共同的特性就是集合的唯一性.TreeMap更是多了一个排序的功能.
3. hashCode和equal()是HashMap用的 因为无需排序所以只需要关注定位和唯一性即可.
   a. hashCode是用来计算hash值的,hash值是用来确定hash表索引的.
   b. hash表中的一个索引处存放的是一张链表, 所以还要通过equal方法循环比较链上的每一个对象才可以真正定位到键值对应的Entry.
   c. put时,如果hash表中没定位到,就在链表前加一个Entry,如果定位到了,则更换Entry中的value,并返回旧value
4. 由于TreeMap需要排序,所以需要一个Comparator为键值进行大小比较.当然也是用Comparator定位的.
   a. Comparator可以在创建TreeMap时指定
   b. 如果创建时没有确定,那么就会使用key.compareTo()方法,这就要求key必须实现Comparable接口.
   c. TreeMap是使用Tree数据结构实现的,所以使用compare接口就可以完成定位了.

## 注意：

1. Collection没有get()方法来取得某个元素。只能通过iterator()遍历元素。list 有
2. Set和Collection拥有一模一样的接口。
3. List，可以通过get()方法来一次取出一个元素。使用数字来选择一堆对象中的一个，get(0)…。(add/get)
4. 一般使用ArrayList。用LinkedList构造堆栈stack、队列queue。
5. Map用 put(k,v) / get(k)，还可以使用containsKey()/containsValue()来检查其中是否含有某个key/value。HashMap会利用对象的hashCode来快速找到key。 * hashing哈希码就是将对象的信息经过一些转变形成一个独一无二的int值，这个值存储在一个array中。我们都知道所有存储结构中，array查找速度是最快的。所以，可以加速查找。发生碰撞时，让array指向多个values。即，数组每个位置上又生成一个梿表。
6. Map中元素，可以将key序列、value序列单独抽取出来。
   使用keySet()抽取key序列，将map中的所有keys生成一个Set。
   使用values()抽取value序列，将map中的所有values生成一个Collection。
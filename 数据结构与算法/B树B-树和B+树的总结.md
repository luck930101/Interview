## 总结

利用平衡树的优势加快查询的稳定性和速度；
B+树的数据都存储在叶子结点中，分支结点均为索引，查询时只需要扫描叶子节点，常用于数据库索引；

B树其分支结点和叶子节点都存储着数据，查询时需要进行一个遍历，常用于文件索引；

**B树和B+树区别：**
关键字数量不同：B+树分支结点M个关键字，叶子节点也有M个；B树分支结点则存在 k-1 个关键码
数据存储位置不同：B+树数据存储在叶子结点上；B树存储在每个结点上；
查询不同：B+树是从根节点到叶子节点的路径；B树是只需要找到数据就可以
分支节点存储信息不同：B+树存索引信息；B树存的是数据关键字

**小结：**
**B树：**二叉树，每个结点只存储一个关键字，等于则命中，小于走左结点，大于走右结点；

**B-树：**多路搜索树，每个结点存储M/2到M个关键字，非叶子结点存储指向关键字范围的子结点；所有关键字在整颗树中出现，且只出现一次，非叶子结点可以命中；

**B+树：**在B-树基础上，为叶子结点增加链表指针，所有关键字都在叶子结点中出现，非叶子结点作为叶子结点的索引；B+树总是到叶子结点才命中；

**B\*树：** 在B+树基础上，为非叶子结点也增加链表指针，将结点的最低利用率从1/2提高到2/3；

## 详细说明

## 为什么使用B树？



B类树是平衡树，每个结点到叶子结点的高度都是相同，这也保证了每个查询是稳定的，查询的时间复杂度时long2(n)；
其次是构造一个多阶B类树，然后在尽量多的在结点上存储相关的信息，保证层数尽量的少，以便后面我们可以更快的找到信息；
**总结：利用平衡树的优势加快查询的稳定性和速度。**

## B树简介

B-Tree，一个 m 阶的B树满足以下条件：

1. 每个结点至多拥有m棵子树；

2. 根结点至少拥有两颗子树（存在子树的情况下）；

3. 除了根结点以外，其余每个分支结点至少拥有 m/2 棵子树；

4. 所有的叶结点都在同一层上；

5. 有 k 棵子树的分支结点则存在 k-1 个关键码，关键码按照递增次序进行排列；

6. 关键字数量需要满足ceil(m/2)-1 <= n <= m-1；

   

   ![img](https://upload-images.jianshu.io/upload_images/5959612-b81be8294621eb26.png)

   B-Tree

   B树上大部分的操作所需要的磁盘存取次数和B树的高度是成正比的，在B树中可以检查多个子结点，由于在一棵树中检查任意一个结点都需要一次磁盘访问，所以B树避免了大量的磁盘访问。

## 操作

B树可视化的网站：[B-Trees]
([https://www.cs.usfca.edu/~galles/visualization/BTree.html](https://link.jianshu.com?t=https%3A%2F%2Fwww.cs.usfca.edu%2F~galles%2Fvisualization%2FBTree.html))
假定对高度为h的m阶B树进行操作。

### 插入

新结点一般插在第h层，通过搜索找到对应的结点进行插入，那么根据即将插入的结点的数量又分为下面几种情况。

- 如果该结点的关键字个数没有到达m-1个，那么直接插入即可；
- 如果该结点的关键字个数已经到达了m-1个，那么根据B树的性质显然无法满足，需要将其进行分裂。分裂的规则是该结点分成两半，将中间的关键字进行提升，加入到父亲结点中，但是这又可能存在父亲结点也满员的情况，则不得不向上进行回溯，甚至是要对根结点进行分裂，那么整棵树都加了一层。

其过程如下：



![img](https://upload-images.jianshu.io/upload_images/5959612-c11df32046f7c405.jpg)



![img](https://upload-images.jianshu.io/upload_images/5959612-c347422b9a94f5bb.jpg)



![img](https://upload-images.jianshu.io/upload_images/5959612-b979b0489ef0a576.jpg)





![img](https://upload-images.jianshu.io/upload_images/5959612-d9cc5aa6b00fae0d.jpg)



### 删除

同样的，我们需要先通过搜索找到相应的值，存在则进行删除，需要考虑删除以后的情况，

- 如果该结点拥有关键字数量仍然满足B树性质，则不做任何处理；
- 如果该结点在删除关键字以后不满足B树的性质（关键字没有到达ceil(m/2)-1的数量），则需要向兄弟结点借关键字，这有分为兄弟结点的关键字数量是否足够的情况。 
  - 如果兄弟结点的关键字足够借给该结点，则过程为将父亲结点的关键字下移，兄弟结点的关键字上移；
  - 如果兄弟结点的关键字在借出去以后也无法满足情况，即之前兄弟结点的关键字的数量为ceil(m/2)-1，借的一方的关键字数量为ceil(m/2)-2的情况，那么我们可以将该结点合并到兄弟结点中，合并之后的子结点数量少了一个，则需要将父亲结点的关键字下放，如果父亲结点不满足性质，则向上回溯；
- 其余情况参照BST中的删除。

其过程如下：



![img](https://upload-images.jianshu.io/upload_images/5959612-82ca66cb555eeaa6.jpg)



![img](https://upload-images.jianshu.io/upload_images/5959612-3d9383c247d3112b.jpg)



![img](https://upload-images.jianshu.io/upload_images/5959612-0ecb25e96e2f6210.jpg)

#### B树的优缺点

B树主要的优点是相对于二叉树,每个节点包括更多的关键字,所以其树高相对较低,查找效率很高.

# B-树

是一种多路搜索树（并不是二叉的）：
 1.定义任意非叶子结点最多只有M个儿子；且M>2；
 2.根结点的儿子数为[2, M]；
 3.除根结点以外的非叶子结点的儿子数为[M/2, M]；
 4.每个结点存放至少M/2-1（取上整）和至多M-1个关键字；（至少2个关键字）
 5.非叶子结点的关键字个数=指向儿子的指针个数-1；
 6.非叶子结点的关键字：K[1], K[2], …, K[M-1]；且K[i] < K[i+1]；
 7.非叶子结点的指针：P[1], P[2], …, P[M]；其中P[1]指向关键字小于K[1]的子树，P[M]指向关键字大于K[M-1]的子树，其它P[i]指向关键字属于(K[i-1], K[i])的子树；
 8.所有叶子结点位于同一层；

如：（M=3）





![img](https://upload-images.jianshu.io/upload_images/5959612-1225dc409bbdbd53.png)



B-树的搜索，从根结点开始，对结点内的关键字（有序）序列进行二分查找，如果命中则结束，否则进入查询关键字所属范围的儿子结点；重复，直到所对应的儿子指针为空，或已经是叶子结点； ‍

B-树的特性：
 1.关键字集合分布在整棵树中；
 2.任何一个关键字出现且只出现在一个结点中；
 3.搜索有可能在非叶子结点结束；
 4.其搜索性能等价于在关键字全集内做一次二分查找；
 5.自动层次控制；

# B+树

## 为什么要B+树

B+树是B-树的变体，也是一种多路搜索树：

1.其定义基本与B-树同，除了：
 2.非叶子结点的子树指针与关键字个数相同；
 3.非叶子结点的子树指针P[i]，指向关键字值属于[K[i], K[i+1])的子树（B-树是开区间）；
 5.为所有叶子结点增加一个链指针；
 6.所有关键字都在叶子结点出现；

如：（M=3）





![img](https://upload-images.jianshu.io/upload_images/5959612-40926cd74ad0bc6c.png)

B+的搜索与B-树也基本相同，区别是B+树只有达到叶子结点才命中（B-树可以在非叶子结点命中），其性能也等价于在关键字全集做一次二分查找；

B+的特性：
 1.所有关键字都出现在叶子结点的链表中（稠密索引），且链表中的关键字恰好是有序的；
 2.不可能在非叶子结点命中；
 3.非叶子结点相当于是叶子结点的索引（稀疏索引），叶子结点相当于是存储（关键字）数据的数据层；
 4.更适合文件索引系统；



### B+树的优点

1、**B+树的层级更少**：相较于B树B+每个非叶子节点存储的关键字数更多，树的层级更少所以查询数据更快；

2、**B+树查询速度更稳定**：B+所有关键字数据地址都存在**叶子**节点上，所以每次查找的次数都相同所以查询速度要比B树更稳定;

3、**B+树天然具备排序功能**：B+树所有的叶子节点数据构成了一个有序链表，在查询大小区间的数据时候更方便，数据紧密性很高，缓存的命中率也会比B树高。

4、**B+树全节点遍历更快**：B+树遍历整棵树只需要遍历所有的叶子节点即可，，而不需要像B树一样需要对每一层进行遍历，这有利于数据库做全表扫描。

B树相对于B+树的优点是，如果经常访问的数据离根节点很近，而B树的非叶子节点本身存有关键字其数据的地址，所以这种数据检索的时候会要比B+树快。

# B树和B+树的区别

这都是由于B+树和B具有这不同的存储结构所造成的区别，以一个m阶树为例。

1. 关键字的数量不同；B+树中分支结点有m个关键字，其叶子结点也有m个，其关键字只是起到了一个索引的作用，但是B树虽然也有m个子结点，但是其只拥有m-1个关键字。
2. 存储的位置不同；B+树中的数据都存储在叶子结点上，也就是其所有叶子结点的数据组合起来就是完整的数据，但是B树的数据存储在每一个结点中，并不仅仅存储在叶子结点上。
3. 分支结点的构造不同；B+树的分支结点仅仅存储着关键字信息和儿子的指针（这里的指针指的是磁盘块的偏移量），也就是说内部结点仅仅包含着索引信息。
4. 查询不同；B树在找到具体的数值以后，则结束，而B+树则需要通过索引找到叶子结点中的数据才结束，也就是说B+树的搜索过程中走了一条从根结点到叶子结点的路径。

# B*树

**是B+树的变体，在B+树的非根和非叶子结点再增加指向兄弟的指针；**





![img](https://upload-images.jianshu.io/upload_images/5959612-26c5a6e59af3ea4a.png)

 ‍



B*树定义了非叶子结点关键字个数至少为(2/3)*M，即块的最低使用率为2/3（代替B+树的1/2）；

B+树的分裂：当一个结点满时，分配一个新的结点，并将原结点中1/2的数据复制到新结点，最后在父结点中增加新结点的指针；B+树的分裂只影响原结点和父结点，而不会影响兄弟结点，所以它不需要指向兄弟的指针；

B*树的分裂：当一个结点满时，如果它的下一个兄弟结点未满，那么将一部分数据移到兄弟结点中，再在原结点插入关键字，最后修改父结点中兄弟结点的关键字（因为兄弟结点的关键字范围改变了）；如果兄弟也满了，则在原结点与兄弟结点之间增加新结点，并各复制1/3的数据到新结点，最后在父结点增加新结点的指针；

所以，B*树分配新结点的概率比B+树要低，空间使用率更高；

# 小结

B树：二叉树，每个结点只存储一个关键字，等于则命中，小于走左结点，大于走右结点；

B-树：多路搜索树，每个结点存储M/2到M个关键字，非叶子结点存储指向关键字范围的子结点；

所有关键字在整颗树中出现，且只出现一次，非叶子结点可以命中；

B+树：在B-树基础上，为叶子结点增加链表指针，所有关键字都在叶子结点中出现，非叶子结点作为叶子结点的索引；B+树总是到叶子结点才命中；

B*树：在B+树基础上，为非叶子结点也增加链表指针，将结点的最低利用率从1/2提高到2/3；
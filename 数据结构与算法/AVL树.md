# AVL树简介

AVL树是被最先发明的一种较为简单的平衡二叉查找树。

它的特点是：

1.本身首先是一棵二叉查找树。

2.带有平衡条件：每个结点的左右子树的高度之差的绝对值（平衡因子LoadFactor）最多为1。

（根结点的高度最高，最底层的叶结点的高度最低且为1。由叶结点向上到树的根结点，树的高度不断增加。例如，只有一个结点的树，该结点即是根结点，高度为1；有两个结点的树，叶结点的高度为1，根结点的高度为2。一棵树总的高度与深度相同，但是树中同一个结点的高度与深度互补。）

优点：

无论是查找、插入或删除，它在最坏情况下的时间复杂度均为O（logN），空间复杂度为O(N)

缺点：引入了平衡因子的概念之后，需要封装更多的信息。其实测复杂度与理论值尚有差距。

![img](https://img-blog.csdn.net/20180928195631402?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3N1bl9sbQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

上面的两张图片，左边的是AVL树，它的任何节点的两个子树的高度差别都小于等于1；而右边的不是AVL树，因为结点7的两颗子树的高度相差为2(以2为根节点的树的高度是3，而以8为根节点的树的高度是1)。 

AVL树的查找、插入和删除在平均和最坏情况下都是O(logn)。

在对AVL树进行插入或删除一个结点之后，会可能导致树中某个结点的左右子树的高度之差超过1，从而破坏了AVL树的适度平衡。因此，为了让它重新回到平衡状态，需要采取额外的操作。

# 重平衡操作

在AVL树中进行插入或者删除一个结点之后，可能会导致AVL树的失衡。AVL树失衡的状态一共可以分为以下四种：

![img](https://img-blog.csdn.net/20180928201121198?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3N1bl9sbQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##  1、LL情况

如下图所示，进行一次右旋转RotateRight就可以恢复树的平衡。

![img](https://img-blog.csdnimg.cn/20190428212939101.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3N1bl9sbQ==,size_16,color_FFFFFF,t_70)

 

```java
//LL情况
	private Node rotateRight(Node node) {
		Node temp = node.left;
		node.left = temp.right;
		temp.right = node;
		node.height = max(height(node.left), height(node.right)) + 1;
		temp.height = max(height(temp.left), height(temp.right)) + 1;
		return temp;
	}

```

## 2、RR情况

如下图所示，进行一次左旋转RotateLeft就可以恢复树的平衡。

![img](https://img-blog.csdnimg.cn/20190428213555394.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3N1bl9sbQ==,size_16,color_FFFFFF,t_70)

```java
//RR情况
	private Node rotateLeft(Node node) {
		Node temp = node.right;
		node.right = temp.left;
		temp.left = node;
		node.height = max(height(node.left), height(node.right)) + 1;
		temp.height = max(height(temp.left), height(temp.right)) + 1;
		return temp;
	}

```

 

## 3、LR情况

如下图所示，先对结点N2进行一次左旋转，再对N1结点进行一次右旋转就可以恢复树的平衡。

![img](https://img-blog.csdnimg.cn/20190428220018525.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3N1bl9sbQ==,size_16,color_FFFFFF,t_70)

```java
//LR情况
	private Node LR(Node node) {
		node.left = rotateLeft(node.left);
		return rotateRight(node);
	}

```

##  4、RL情况

如下图所示，先对N2结点进行一次右旋转，再对N1结点进行一次左旋转就可以恢复树的平衡。

![img](https://img-blog.csdnimg.cn/20190428215410501.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3N1bl9sbQ==,size_16,color_FFFFFF,t_70)

```java
//RL情况
	private Node RL(Node node) {
		node.right = rotateRight(node.right);
		return rotateLeft(node);
	}
```

#  AVL树完整Java实现

下面是基于Java实现的AVL树。此处规定一个空节点的高度为-1，所有叶子节点的高度为0。

```java
public class AVLTree<Key extends Comparable<Key>, Value> {
	
	private Node root;
	
	private class Node {
		Key key;
		Value val;
		int height;
		Node left,right;
		
		public Node(Key key, Value val, int height) {
			this.key = key;
			this.val = val;
			this.height = height;
		}
	}
	
	public void put(Key key, Value val) {
		root = put(root, key, val);
	}
	
	private Node put(Node node, Key key, Value val) {
		if(node == null)
			return new Node(key, val, 0);
		int cmp = key.compareTo(node.key);
		if(cmp > 0) {
			node.right = put(node.right, key, val);
		} else if(cmp < 0) {
			node.left = put(node.left, key, val);
		} else {
			node.val = val;
		}
		node = banlance(node);
		return node;
	}
	
	public Value delete(Key key) {
		Node node = delete(root, key);
		if(node == null)
			return null;
		return node.val;
	}
	
	private Node delete(Node node, Key key) {
		if(key == null || node == null)
			return null;
		int cmp = key.compareTo(node.key);
		if(cmp < 0) {
			node.left = delete(node.left, key);
		} else if(cmp > 0) {
			node.right = delete(node.right, key);
		} else {
			if(node.left != null && node.right != null) {
				Node temp = node;
				node = min(node.right);
				node.left = temp.left;
				node.right = removeMin(temp.right);
			} else {
				node = (node.left == null ? node.right : node.left);
			}
		}
		node = banlance(node);
		return node;
	}
	
	private Node banlance(Node n) {
		if(n == null)
			return n;
		if(height(n.left) - height(n.right) > 1) {
			if(height(n.left.left) >= height(n.left.right)) {
				n = rotateRight(n);
			} else {
				n = LR(n);
			}
		} else if(height(n.right) - height(n.left) > 1) {
			if(height(n.right.right) >= height(n.right.left)) {
				n = rotateLeft(n);
			} else {
				n = RL(n);
			}
		}
		n.height = max(height(n.left), height(n.right)) + 1;
		return n;
	}
	
	//LL情况
	private Node rotateRight(Node node) {
		Node temp = node.left;
		node.left = temp.right;
		temp.right = node;
		node.height = max(height(node.left), height(node.right)) + 1;
		temp.height = max(height(temp.left), height(temp.right)) + 1;
		return temp;
	}
	
	//RR情况
	private Node rotateLeft(Node node) {
		Node temp = node.right;
		node.right = temp.left;
		temp.left = node;
		node.height = max(height(node.left), height(node.right)) + 1;
		temp.height = max(height(temp.left), height(temp.right)) + 1;
		return temp;
	}
	
	//LR情况
	private Node LR(Node node) {
		node.left = rotateLeft(node.left);
		return rotateRight(node);
	}
	
	//RL情况
	private Node RL(Node node) {
		node.right = rotateRight(node.right);
		return rotateLeft(node);
	}
	
	//以node为根结点的子树的高度,规定空子树的高度为-1
	private int height(Node node) {
		if(node == null)
			return -1;
		return node.height;
	}
	
	private Node removeMin(Node node) {
		if(node == null)
			return null;
		if(node.left == null)
			return node.right;
		node.left = removeMin(node.left);
		node.height = max(height(node.left), height(node.right)) + 1;
		return node;
	}
	
	private Node min(Node node) {
		if(node == null)
			return node;
		while(node.left != null)
			node = node.left;
		return node;
	}
	
	private int max(int a, int b) {
		return a > b ? a : b;
	}
 
}

```

 

 
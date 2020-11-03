```java
import java.util.HashMap;
public class LRUCache {
	
HashMap<Integer, LRUNode > map;
int capacity;
int size;
LRUNode dummyhead;
LRUNode dummytail;

public LRUCache(int capacity){
	this.capacity = capacity;
	this.map = new HashMap<Integer, LRUNode>();
	this.size = 0;
	this.dummyhead = new LRUNode(0,0); 
	this.dummytail = new LRUNode(0,0); 
	
	dummyhead.next = dummytail;
	dummytail.prev = dummyhead;
}
public void put(int key, int value){
	if(this.get(key)!= -1){
		this.map.get(key).value = value;
		return;
	}
	else{
		LRUNode newnode = new LRUNode(key,value);

	if(this.size == this.capacity){
			remove(dummyhead.next);
		}
		add(newnode);
	}
}

public int get(int key){
	LRUNode node = map.get(key);
	if(node == null){
		return -1;
	}
	
	remove(node);
	add(node);
	
	return node.value;
}

public void add(LRUNode node){
	node.prev = dummytail.prev;
	node.next = dummytail;
	dummytail.prev.next = node;
	dummytail.prev= node;
	this.map.put(node.key, node);
	this.size++;
	
}
public void remove(LRUNode node){
	LRUNode removednode = map.get(node.key);
	removednode.prev.next = removednode.next;
	removednode.next.prev = removednode.prev;
	this.map.remove(node.key);
	this.size--;
}

public static void main(String[] args) {
	// TODO Auto-generated method stub
	
	LRUCache cache = new LRUCache(4);
	
	cache.put(1,1);
	cache.put(2,2);
	cache.put(3,3);
	cache.put(4,4);
	cache.put(5,5);
	
	System.out.println(cache.get(1));
	System.out.println(cache.get(2));
	System.out.println(cache.get(3));
	System.out.println(cache.get(4));
	System.out.println(cache.get(5));

	System.out.println(cache.get(2));
	
	cache.put(6,6);
	cache.put(7,7);
	cache.put(8,8);

	System.out.println("**********************");
	System.out.println(cache.get(1));
	System.out.println(cache.get(2));
	System.out.println(cache.get(3));
	System.out.println(cache.get(4));
	System.out.println(cache.get(5));
	System.out.println(cache.get(6));
	System.out.println(cache.get(7));
	System.out.println(cache.get(8));
	System.out.println(cache.get(9));
	System.out.println(cache.get(10));
	System.out.println("**********************");

	}
}
```


今天中午吃饭闲暇，和朋友聊到了如果不使用Math.sqrt方法，该怎么通过Java实现同样的功能，我们各自发表了下意见。

以下是我和朋友二人的解法思路：

1、朋友采用的是先确定当前数所处的最小整数区间，然后再通过二分法来进行判断检测。

2、我当时的想法是直接通过二分法进行判断检测，然后判断精度是否到达1e-7进行处理；

随后，回到宿舍后，想到了通过牛顿迭代法进行求值，而且速度上更快了一些。然后，索性就通过三种方式实现了该方法，

代码如下：

方法一（二分法）：



```java
	public static double sqrt(double t, Double precise) {
		double low = 0, high = t, middle, squre,
				prec = precise != null ? precise : 1e-7;
		if ( t < 0 ) {
			throw new RuntimeException("Negetive number cannot have a sqrt root.");
		}
		
		while ( high - low > prec ) {
			middle = ( low + high ) / 2;
			squre = middle * middle;
			
			if ( squre > t ) {
				high = middle;
			} else {
				low = middle;
			}
		}
		return ( low + high ) / 2;
	}
```


解法二（牛顿迭代法）：



```java
public static double sqrt_ ( double t, Double precise) {
		double x0 = t, x1, differ,
				prec = precise != null ? precise : 1e-7;
		
		while ( true ) {
			x1 = ( x0 * x0 + t ) / ( 2 * x0 );
			differ = x1 * x1 - t;
			
			if ( differ <= prec && differ >= -prec ) {
				return x1;
			}
			x0 = x1;
		}
	}
```


解法三（也是最准确的，针对朋友解法的优化）：



```java
	public static float sqrtRoot(float m) {
	   if ( m == 0 ) {
		   return 0;
	   }
		
	   float i = 0;
	   float x1, x2 = 0;
	   while ( ( i * i ) <= m ) {
	          i += 0.1;
	   }
	   x1 = i;
	   for ( int j = 0; j < 10; j++) {
	      x2 = m;
	      x2 /= x1;
	      x2 += x1;
	      x2 /= 2;
	      x1 = x2;
	   }
	   return x2;
	}
```



该解法的测试代码：



```java
public static void main(String[] args) {
		for ( int i = 0; i <= 10; i++ ) {
			System.out.println(i + " : " + sqrtRoot(i));
		}
	}
```



一下附上该解法的测试结果图：

![img](https://img-blog.csdn.net/20161220141954222?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMTc3NzYyODc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)


**以上便是Java不使用Math.sqrt方法实现的求平方根解法。**
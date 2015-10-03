- 计算中值时，使用`int mid = start + (end - start) / 2`来避免overflow

- [Squareroot of a Number](http://www.ardendertat.com/2012/01/26/programming-interview-questions-27-squareroot-of-a-number/)
实现sqrt(x)时，常规binary可解，log复杂度，还有一种数学方法，可以constant时间解决

- 实现一个带有min的Stack，可以做O(1)的push, pop, peek和getMin 

  - 可以用单链表或者自建一个链表类
  ```
  class Node {
  	int value;
  	int min;
  	Node next;
   
  	Node(int x) {
  		value = x;
  		next = null;
  		min = x;
  	}
  }
  ```
  
  - 或者使用两个stack， 一个放元素，另一个放对应的最小值
  

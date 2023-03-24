# 자료구조

## 자료구조의 분류
### 선형 구조와 비선형 구조로 선형 구조는 리스트(선형리스트와 연결리스트), 스택, 큐, 데큐, 비선형구조는 트리와 그래프가 있다. 
![image](https://user-images.githubusercontent.com/107795830/226811565-79894bc0-33a0-4cd8-aee0-da4fca18f475.png)

-----

* ## 선형 구조
  * **리스트(List)**
    * **선형 리스트(Linear List)**
    * **연결 리스트(Linked List)**
  * **스택(Stack)** - LIFO(Last In First Out)
  * **큐(queue)** - FIFO(First In First out)
* ## 비선형 구조
  * 트리(Tree)
    * ** 이진 트리(binary tree)

-----

* ## 선형 리스트(Linear List)
  * 선형 리스트는 **배열(Array)과 같이 연속되는 기억장소에 저장되는 리스트이다.**
  * 선형 리스트의 대표적인 구조 -> **배열(Array)**
* ### 특징
  * 가장 간단한 자료구조이다.
  * **접근 속도가 빠르다.**
  * **고정된 크기로 있기 때문에 비 효율적이다.**
  * **삽입 및 삭제 시 자료의 이동이 필요하기 때문에 번거로운 작업이 필요하다.**
* ### 자료와 자료는 빈 공간 없이 차례대로 연결된다.

* ### 배열(Array)
  * 여러개의 데이터를 저장시키기 위한 것이다.
  * 장점 : 기억 공간의 밀도가 좋고 액세스(access) 처리 시간이 빠르다.
  * 단점 : 삽입 삭제가 불편하고 기억 공간에 인접해 있어야 한다.   
    삽입이나 삭제할 위치 이후의 전체적인 데이터 이동을 해야한다.
  
![image](https://user-images.githubusercontent.com/107795830/226501107-b5f90bf8-426e-4c38-924c-9d6c50708e9f.png)

-----


* ## 연결 리스트(Linked List) 
  * 연결 리스트는 자료들을 반드시 연속적으로 배열시키지 않는다. 
  * **동적 메모리에 할당된 링크에 의해 연결된 유한 개수의 데이터 원소들**
* ### 특징
  * 링크 값을 변화 시키는 것 만으로 **노드의 삽입 삭제가 용이하다.**
  * **기억공간이 연속적으로 놓여 있지 않아도 저장이 가능하다.**
  * **연결을 위한 링크(포인터) 부분이 필요하기 떄문에 순차 리스트에 비해 기억공간 효율이 좋지 않다.**
  * **연결을 할 때 포인터를 찾는 시간이 필요하여 접근하는 속도가 느리다.**
  * **트리를 표현할 때 가장 적합한 자료이다.**
  
* ### 노드(node)
### 자료와 포인터를 갖고 있는 것을 노드(node)라고 한다.
![image](https://user-images.githubusercontent.com/107795830/226497844-0d4ecdf7-bb33-409f-a05b-e6668acabad8.png)
![image](https://user-images.githubusercontent.com/107795830/226497920-c94e40ae-183e-4452-b02f-74435258d212.png)

* ### 희소 행렬
**희소 행렬이란 요소 중에 0으로 저장 되어 있는 형태로 기억 장소를 절약하기 위해 Linked List를 이용하여 저장한다.**

-----

* ## 스택(Stack) - LIFO(Last In First Out)
  * 스택은 리스트의 한쪽 끝 자료의 삽입 및 삭제가 이루어지는 구조이다.
  * **먼저 삽입된 자료가 맨 나중에 삭제되는 후입 선출로 Last In First Out 방식이다.**
  * Push : 삽입 , Pop : 삭제
* ### 특징
  * **Push**
    * 스택의 크기를 초과하기 전까지 삽입을 한다.
    * 스택의 크기를 초과하여 삽입을 할 경우 OverFlow가 발생한다.
  * **Pop**
    *  스택이 비어있을 때까지 삭제를 한다.
    *  스택이 비어있을 경우 UnderFlow가 발생한다.

* ### Java로 스택 구현
```java
import java.util.EmptyStackException;

public class IntStack {
	// 스택용 배열
	private int[] stk;
	// 스택의 크기
	private int capacity;
	// 스택 포인터
	private int ptr;
	
	//--- 실행시 예외 : 스택이 비어있음 ---//
	public class EmptyIntStackExeption extends RuntimeException{
		public EmptyIntStackExeption() { }
	}
	
	//--- 실행시 예외 : 스택이 가득 차있음 ---//
	public class OverflowIntStackExeption extends RuntimeException{
		public OverflowIntStackExeption() { }
	}
	
	//--- 생성자(constreuctor) ---//
	public IntStack(int maxlen) {
		ptr = 0;
		capacity = maxlen;
		try 
		{
			// 스택 본체용 배열을 생성
			stk = new int[capacity];
		}
			// 생성할 수 없음
		catch (OutOfMemoryError e)
		{
			  capacity = 0;
		}
	}
	
	//--- 스택에 x를 푸시 ---//
	public int push(int x) throws OverflowIntStackExeption
	{
		if (ptr >= capacity)
			// 스택이 가득 차있음
			throw new  OverflowIntStackExeption();
		return stk[ptr++] = x;
	}
	
	//--- 스택에서 데이터를 팝(정상에 있는 데이터를 꺼냄) ---//
	public int pop(int x) throws EmptyStackException
	{
		if (ptr == 0)
			// 스택이 비어있음
			throw new EmptyStackException();
		return stk[--ptr];
	}
}
```
-----

## 큐(queue) - FIFO(First In First out)
* #### 큐(queue)는 한쪽 방향으로 데이터가 삽입되고 반대 방향으로 데이터가 삭제되는 먼저 들어온 데이터가 먼저 나가는 선입 선출(First In First Out) 구조이다.
* #### 특별한 우선 순위가 없을 경우에는 먼저 들어온 프로세스가 먼저 처리된다.
* #### 예를 들면 계산대에서 먼저 계산대에 온 고객이 먼저 계산하고 나가는 것이다.

![image](https://user-images.githubusercontent.com/107795830/226809992-fa685ecd-5df8-4365-b5ed-0b17c4bd4cd6.png)

### 아무 것도 없는 큐에서 데이터 삭제가 일어나면 UnderFlow Error 발생하고,   
### 반대로 큐에 다 채워져 있는 상태에서 삽입 시 OverFlow Error가 발생한다.

* ### 프런트(F, Front)
  * 가장 먼저 삽입된 자료의 기억 장소를 가리키는 포인터이다.
  * 삭제 작업을 할 때 사용한다.
* ### 리어(R, Rear)
  * 가장 마지막에 삽입된 자료의 기억 장소를 가리키는 포인터이다.
  * 삽입 작업을 할 때 사용한다.
* ### Queue의 응용 분야
  * 창구 업무나 택시 정거장, 버스 정류장 등 서비스 순서를 기다리는 등의 대기 행열의 처리에 사용한다.
  * 운영 체제의 작업 스케쥴링에 사용된다.
 
  ![image](https://user-images.githubusercontent.com/107795830/226809777-cd0918e1-9593-4a90-8cfe-ebdba786df57.png)
  
* ### Java로 큐 구현
```java
package sungil2023_03_algo;

public class IntQueue {
	private int[] que; 	  // 큐용 배열
	private int capacity;     // 큐의 크기
	private int front;	  // 맨 처음 요소 커서
	private int rear;	  // 맨 끝 요소 커서
	private int num;	  // 현재 데이터 개수
	
	//--- 실행시 예외 : 큐가 비어있음 ---//
	public class EmptyIntQueueException extends RuntimeException{
		public EmptyIntQueueException() {}
	}
	
	//--- 실행시 예외 : 큐가 가득 차있음 ---//
	public class OverflowIntQueueException extends RuntimeException{
		public OverflowIntQueueException() {}
	}
	
	//--- 생성자(constructor) ---//
	public IntQueue(int maxlen) {
		num = front = rear = 0;
		capacity = maxlen;
		try {
			// 큐 본체용 배열을 생성
			que = new int[capacity];
		}
		catch (OutOfMemoryError e) {
			// 생성할 수 없음
			capacity = 0;
		}
	}
	
	//--- 큐에 데이터를 인큐 ---//
	public int enque(int x) throws OverflowIntQueueException {
		if (num >= capacity) {
			throw new OverflowIntQueueException(); // 큐가 가득 찼음
		}
		que[rear++] = x;
		num++;
		if(rear == capacity) {
			rear = 0;
		}
		return x;
	}
	
	//--- 큐에서 데이터를 디큐 ---//
	public int deque() throws EmptyIntQueueException{
		if (num <= 0) {
			throw new EmptyIntQueueException(); // 큐가 비어있음
		}
		int x = que[front++];
		num--;
		if(front == capacity) {
			front = 0;
		}
		return x;
	}

}
```

-----

중복된 값은 허용하지 않는다.

![image](https://user-images.githubusercontent.com/107795830/227129934-4a65a246-5d80-4ece-aacc-3e25a03745a8.png)

## 트리(Tree)

* ### 트리는 정점(Node)과 선분(branch)를 이용하여 사이클을 이루지 않도록 구성한 그래프(Graph)의 특수한 형태이다.
* ### 트리 관련 용어
  * ### 노드(Node)
     * #### 트리의 기본이면서 자료 항목과 다른 항목에 대한 가지(Branch)를 합친 것이다.
  * ### 깊이(Depth, Height)
     * #### 트리에서 노드가 가질 수 있는 최대의 레벨을 뜻한다.
  * ### 디그리(Degree)
     * #### 차수로 각 노드에서 뻗어 나온 가지의 수 이다.
     > A = 3, B = 2, C = 1, D = 3
  * ### 단말 노드(Terminal Node, = 잎(Leaf) 노드 )
     * #### 자식이 없는 노드 즉, Degree(차수)가 0인 노드
     > K L, F, G, M, I, J
  * ### 비단말 노드(Non-Terminal Node)
     * #### 자식이 하나라도 있는 노드, Degree(차수)가 0이 아닌 노드
     > A, B, C, D, E, H
  * ### 조상 노드(Ancestors Node) 
     * #### 임의의 노드에서 근 노드에 이르는 경로상에 있는 노드들
   	> M의 조상 노드는 H, D, A}
  * ### 자식 노드(Son Node) 
     * #### 어떤 노드에 연결된 다음 레벨의 노드들
   	> D의 자식 노드는 H, I, J
  * ### 부모 노드(Parent Node) 
     * #### 어떤 노드에 연결된 이전 레벨의 노드들
   	> E, F의 부모 노드는 B
  * ### 형제 노드(Brother Node, Sibling)
     * #### 동일한 부모를 갖는 노드들
   	> H의 형제 노드는 I, J 

-----

## 이진 트리(binary tree)
![image](https://user-images.githubusercontent.com/107795830/227132887-3294419d-ada8-4b36-9a4b-26adea12b2f1.png)
* ### 모든 노들의 자식 노드가 두 개 이하인 트리를 의미한다. 
* ### 완전 이진 트리(complete binary tree)
   * #### 단말 노드를 제외한 나머지 노드가 2개의 자식을 가지고 있는 트리를 말한다.
    > -> A, B, C, D 노드는 모두 2개의 자식을 가지고 있다.

* #### 이진 트리의 전체 노드의 수를 구하는 방법은 다음과 같이 구하면 된다.
  * 전체 노드의 수 : 2<sup>k</sup> - 1    (k는 레벨)
  * 레벨 k에서의 노드의 수 : 2<sup>k-1</sup>
  
![image](https://user-images.githubusercontent.com/107795830/227390681-7cf33e48-402e-4be7-b07d-ed5211a9f345.png)

* ### 전이진 트리(Complete Binary Tree)
    * ### 전이진 트리는 노드의 수가n개일 때, 정이진 트리의 각 노드에 붙힌 1~n의 일련번호와 1:1 대응되는 트리를 말한다. 중간에 빈 부분이 있으면 전이진 트리가 될 수 없다.
    
![image](https://user-images.githubusercontent.com/107795830/227391027-07166371-3a2b-4c74-8032-3c2121bb87ea.png)

   
* ### 사향 이진 트리(Skewed Binary Tree)
   * #### 사향 이진 트리는 루트 노드로 부터 왼쪽 또는 오른쪽으로만 기울어진 트리, 즉 왼쪽 또는 오른쪽 자식이 없는 노드들로 만 구성된 트리다.
      * #### 왼쪽 사향 이진 트리 : 오른쪽 자식이 없는 노드들로 만 구성된 트리
      * #### 오른쪽 사향 이진 트리 : 왼쪽 자식이 없는 노드들로 만 구성된 트리 
      
 ![image](https://user-images.githubusercontent.com/107795830/227390968-c349500a-d29a-479d-8b6a-ed4e016cc01b.png)
      
* ### 이진 트리(binary tree)의 표현
   * #### 이진 트리는 배열이나 연결 리스트를 이용해서 구현할 수 있다.
   
* ### 이진 트리(binary tree)의 순회
  * #### 이진 트리의 모든 노드를 특정한 순서대로 한 번씩 방문하는 것이다.
  * #### 순회하는 방법은 전위(preorder), 중위(inorder), 후위(postorder) 순회가 있다.
  * #### 전위 순회(Preorder)
      * ##### 노드(루트)를 방문하고 왼쪽 서브 트리, 오른쪽 서브 트리 순으로 방문한다.
          > Root -> Left -> Right
  * #### 중위 순회(Preorder)
       * ##### 왼쪽 서브 트리를 방문하고 노드(루트), 오른쪽 서브 트리 순으로 방문한다.
          > Left -> Root -> Right
  * #### 후위 순회(Postorder)
       * ##### 왼쪽 서브 트리를 방문하고 오른쪽 서브 트리, 노드(루트) 순으로 방문한다.
          > Left -> Right -> Root
* ### 이진 탐색 트리(Binary Search Tree)

	* #### 이진 탐색 트리는 데이터의 삽입, 삭제, 탐색 등이 자주 발생하는 경우에 효율적인 구조로, 이진 트리 이면서 같은 값을 갖는 노드가 없어야 한다.
	* #### 왼쪽 서브 트리에 있는 모든 데이터는 현재 노드(루트)의 값보다 작다.
	* #### 오른쪽 서브 트리에 있는 모든 데이터는 현재 노드(루트)의 값보다 크다.
* ### 데이터 탐색은 루트에서부터 시작한다.
   * #### 루트 노드의 데이터와 찾으려는 데이터를 비교하여 같으면 탐색은 성공하면서 종료된다.
   * #### 루트 노드가 찾으려는 데이터보다 작으면 루트 노드의 오른쪽으로 이동한다.
   * #### 루트 노드가 찾으려는 데이터보다 크면 루트 노드의 왼쪽으로 이동한다.
* ### 이진 트리 삽입
   * #### 이진 트리에서의 삽입은 탐색 동작을 통해 이루어 진다.
   * #### 탐색에 성공하면 삽입은 실패한다, 그 이유는 탐색을 통해 넣으려는 데이터가 있는지 검사하는데 이미 있는 데이터는 삽입 할 수 없기 때문이다.
   * #### 반면에 탐색에 실패하면 삽입을 할 수 있으며, 탐색에 종료된 지점의 데이터를 값으로 하는 노드가 삽입된다.
   * #### 삽입할 위치는 루트 노드에서부터 시작되며 삽입할 노드의 데이터가 비교하는 노드의 데이터보다 작으면 왼쪽 서브 트리로 진행하고 크면 오른쪽 서브 트리로 진행한다.
   
* #### 데이터가 20인 노드를 탐색 하는 과정을 살펴보면
 > 7 -> 11 -> 15  순으로 이동하게 되는데 못 찾으면 실패이므로 삽입을 할 수 있다.
 
![image](https://user-images.githubusercontent.com/107795830/227394039-6ede98e1-d937-445c-91b3-c67f84a33473.png)

* ### 이진 트리 삭제
   * 이진 탐색 트리에서 노드를 삭제하는 동작은 삭제할 노드의 위치에 따라 세 가지로 구분된다.
 
* #### 삭제할 노드가 단말 노드인 경우
 * ##### 부모 노드에서 삭제할 노드를 가리키는 링크를 제거하면 된다. 
   > 데이터가 6인 노드를 삭제하려면 부모 노드인 데이터가 7인 노드에서 삭제할 노드를 가리키는 링크를 제거
 
![image](https://user-images.githubusercontent.com/107795830/227394645-7a0b4ddc-fc7a-4fff-b01c-582c87795ea3.png)

* #### 삭제할 노드의 자식 노드가 하나인 경우
   * ##### 부모 노드에서 삭제할 노드를 가리키는 링크를 삭제할 노드의 자식 노드를 가리킨다.
   * > 12인 노드를 삭제하려면 데이터가 12인 노드를 삭제하고, 데이터가 12인 노드의 부모 노드, 즉 데이터가 10인 노드가 삭제된 노드의 자식 노드인 데이터 15인 노드를 가리키게 한다.
 
![image](https://user-images.githubusercontent.com/107795830/227395235-74762622-0e01-4479-bbbb-d3a1cb11e4a8.png)

* #### 삭제할 노드의 자식 노드가 두 개인 경우
   * ##### 삭제할 노드의 자식 노드가 두 개인 경우는 조금 복잡하다. 
   * ##### 우선 삭제할 노드를 왼쪽 서브 트리에서 가장 큰 노드 또는 오른쪽 서브 트리에서 가장 작은 노드로 대체한다. 그리고 대체된 원래 노드를 삭제한다.
   > 자식 노드가 두 개인 데이터 10 노드를 삭제하려면 데이터 10 노드를 왼쪽 서브 트리에서 가장 큰 노드인 데이터 7 노드 또는 오른쪽 서브 트리에서 가장 작은 노드인 데이터 12 노드로 대체한다. 만약 오른쪽 서브 트리에서 가장 작은 노드인 데이터 12 노드로 대체한다고 가정하면 (b)와 같이 나타난다. 그리고 대체된 원래의 데이터 12 노드를 삭제하면 (c)와 같은 결과가 나온다.
  


![image](https://user-images.githubusercontent.com/107795830/227395986-143f9191-154d-45a6-9b28-0a39a08ce17d.png)

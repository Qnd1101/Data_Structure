# 선형 구조

* ## 선형구조
  * **리스트(List)**
    * **선형 리스트(Linear List)**
    * **연결 리스트(Linked List)**
  * **스택(Stack)**
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

* ## 스택(Stack)
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
```java
package sungil2023_03_algo;

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
		try {
			// 스택 본체용 배열을 생성
			stk = new int[capacity];
		}
			// 생성할 수 없음
		catch (OutOfMemoryError e) {
			  capacity = 0;
		}
	}
	
	//--- 스택에 x를 푸시 ---//
	public int push(int x) throws OverflowIntStackExeption{
		if (ptr >= capacity)
			// 스택이 가득 차있음
			throw new  OverflowIntStackExeption();
		return stk[ptr++] = x;
	}
	
	//--- 스택에서 데이터를 팝(정상에 있는 데이터를 꺼냄) ---//
	public int pop(int x) throws EmptyStackException{
		if (ptr == 0)
			// 스택이 비어있음
			throw new EmptyStackException();
		return stk[--ptr];
	}
}
```

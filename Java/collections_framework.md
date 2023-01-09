# Collections Framework

### 컬렉션 프레임웍

```
💡 데이터 군을 저장하는 클래스들을 표준화한 설계
다수의 데이터를 다루는 데 필요한 다양하고 풍부한 클래스 제공 
```

Collection → 다수의 데이터, 즉 데이터 그룹 

Framework → 표준화된 프로그래밍 방식


<br>


### 컬렉션 프레임웍의 핵심 인터페이스

- **List** : 순서가 있는 데이터의 집합, 중복 허용
    - ArrayList, LinkedList, Stack, Vector 등
- **Set** : 순서를 유지하지 않는 데이터의 집합, 중복 허용 X
    - HashSet, TreeSet 등
- **Map** : 키와 값의 쌍으로 이루어진 데이터의 집합, 순서는 유지되지 않고, 키는 중복 허용 X, 값은 중복 허용
    - HashMap, TreeMap, Hashtable, Properties 등

<br>

### ArrayList

- List 인터페이스를 구현한다.
- 데이터의 저장 순서가 유지되고 중복을 허용한다.
- Object 배열을 이용한다. → 모든 종류의 객체를 담을 수 있다.
- 기존 Vector를 개선한 것이다. → Vector 보다는 ArrayList를 사용하기!

- containsAll()
- retainAll()
- remove()
- add()
- set()

<br>

### Vector

size = 3, capacity = 5 인 벡터 v가 있다고 가정한다.

- trimToSize() : v의 빈 공간을 없애서 size와 capacity를 같게 한다.
    - size = 3, capacity = 3
- ensureCapacity(6) : v의 capacity가 최소한 6이 되도록 한다.  매개변수는 정수
    - size = 3, capacity = 6
- setSize(7) : v의 size를 7로 설정하고 capacity가 충분하지 않으면 자동으로 2배 증가한다. 매개변수는 정수
    - size = 7, capacity = 12
- clear() : v의 모든 요소를 삭제한다.
    - size =  0, capacity = 0


<br>


### LinkedList

**Linked List** : 불연속적으로 존재하는 데이터를 서로 연결한 형태

- 각 요소들은 자신과 연결된 다음 요소에 대한 참조와 데이터로 구성되어 있다.

```java
Class Node {
	Node next;
	Object obj;
}
```

- 데이터 삭제 : 삭제하고자 하는 요소의 이전 요소가 삭제하고자 하는 요소의 다음 요소를 참조하도록 변경
- 데이터 추가 : 새로운 요소를 생성하고, 추가하고자 하는 위치의 이전 요소의 참조를 새로운 요소에 대한 참조로 변공, 그 다음 요소를 참조하도록 변경

**doubly Linked List** : 이전 요소와 다음 요소의 참조가 모두 가능하다.

**doubly circular Linked List** : 더블 링크드 리스트의 첫번째 요소와 마지막 요소를 서로 연결시킨 것 → 마지막 요소의 다음 요소가 첫번째, 첫번째 요소의 이전 요소가 마지막 요소가 된다.


<br>


### ArrayList와 LinkedList

> **순차적으로 추가/삭제하는 경우는 ArrayList가 LinkedList보다 빠르다**
> **중간 데이터를 추가/삭제하는 경우에는 LinkedList가 ArrayList 보다 빠르다.**
> 

| 컬렉션 | 읽기(접근시간) | 추가/삭제 | 비고 |
| --- | --- | --- | --- |
| ArrayList | 빠르다 | 느리다 | 순차적인 추가/삭제는 더 빠름. 비효율적인 메모리 사용 |
| LinkedList | 느리다 | 빠르다 | 데이터가 많을 수록 접근성이 떨어짐 |

**다루고자 하는 데이터 개수가 변하지 않는 경우라면 ArrayList,  데이터 개수 변경이 잦다면 LinkedList 사용하기**


<br>


### Stack

마지막에 저장한 데이터를 가장 먼저 꺼내는 LIFO(Last In First Out) 구조이다.

→ ArrayList

활용) 수식계산, 수식괄호검사, 워드프로세서의 undo/redo, 웹브라우저의 뒤로/앞으로

- peek() : 최근 추가된(Top) 데이터 조회
- pop() : 최근 추가된(Top) 데이터 삭제
- push() : 데이터 추가
- empty() : stack 값이 비었는지 확인, 비었으면 true, 아니면 false
- search(Object obj) : 인자값으로 받은 데이터의 위치 반환


<br>


### Queue

처음에 저장한 데이터를 가장 먼저 꺼내게 되는 FIFO(First In First Out) 구조이다.

→ LinkedList

활용) 최근 사용문서, 인쇄작업 대기 목록, 버퍼

- offer() : 데이터 추가, 큐가 꽉찬 경우 false를 반환한다.
- remove() : 데이터 삭제, 삭제를 실패한 경우 예외를 반환한다.
- poll() : 데이터 삭제, 삭제를 실패한 경우 false를 반환한다.

> `equalsIgnoreCase` : 대소문자를 구분안한다.
> 
> `equals` : 대소문자를 구분한다.
> 
> → 문자열이 같으면 true, 다르면 false 리턴

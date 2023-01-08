# Java - array

### 배열(array) 
* 동일한 타입의 여러 변수를 하나의 묶음으로 다루는 것이다.
* 배열은 저장 공간이 연속적으로 배치되어 있다.


<br>

### 배열 선언, 생성
**선언** 
* 배열을 다루기 위한 참조변수를 위한 공간을 만든다. (데이터를 저장할 수 있는 공간은 아직 생성되지 않았음)
* 타입[] 변수명;
* 타입 변수명[];

**생성** 
* 값을 저장할 수 있는 실제 저장공간을 생성한다.
* 변수명 = new 타입[길이]

```java
int[] score;    // int형 배열 참조변수 score를 선언 (데이터를 저장할 수 있는 공간x)
score = new int[5];  //'new'에 의해 메모리의 빈 공간에 5개의 int형 데이터를 저장할 수 있는 공간 생성
```

* 배열의 첫 번째 인덱스의 주소는 참조변수에 저장된다.


<br>


**선언과 생성을 동시에**

타입[] 변수명 = new 타입[길이]

```java
int[] score = new int[5]
```


<br>


### 배열 길이, 인덱스

**배열의 요소** : 생성된 배열의 각 저장공간
> 배열명[인덱스]로 접근할 수 있다.
인덱스(index) 범위 : 0 부터 배열의 길이 -1

```java
int[] score = new int[5];
score[0], score[1], score[2], score[3], score[4]
```

* 인덱스의 값은 상수 대신 변수, 수식도 사용할 수 있다.
* 배열의 길이는 int 범위의 양의 정수(0도 포함)이어야 한다.

> 배열의 길이 = 배열이름.length


<br>


### 배열의 초기화

#### 1. 생성과 초기화를 동시에
```java
int[] score = new int[]{50,60,70,80,90};
```

* {} 안의 개수에 따라 배열의 길이가 자동으로 결정되기때문에 배열의 길이를 적지 않아도 된다.
* new int[]를 생략할 수도 있다


```java
int[] score = {50,60,70,80,90}
```

<br>

#### 2. for문을 이용하여 초기화 한다.
```java
int[] score = new int[5];
for(int i = 0; i<score.length; i++) 
   score[i] = i * 10 + 50;
```
<br>

### 배열의 출력
#### 1. for문 이용
#### 2. Arrays.toString(배열이름) 메소드 사용
 -> [첫번째 요소, 두번째 요소, ....]로 반환한다.


* char 배열은 println을 사용하여 출력하면 각 요소가 구분자 없이 출력된다.
```java
char[] arr = {'a', 'b', 'c'};
System.out.println(arr);
```
    
    결과 : abc
       
<br>

### 배열의 복사
#### 1. for문 이용
```java
int[] arr = new int[5];

int[] tmp = new int[arr.length*2];
for(int i = 0; i<arr.length; i++)
	tmp[i] = arr[i]
arr = tmp // tmp에 저장된 주소 값을 arr에 저장한다.
```

#### 2. System.arraycopy() 이용
* 지정된 범위의 값들을 한 번에 통째로 복사한다. 
```java
System.arraycopy(num, 0, newNum, 0, num.length);
//num[0] 에서 newNum[0]으로 num.length개의 데이터 복사
```





  

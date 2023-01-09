# Generics

```
💡 다양한 타입의 객체를 다루는 메서드나 컬렉션 클래스에 컴파일 시의 타입체크를 해주는 기능
   → 객체의 타입을 컴파일 시에 체크하기 때문에 객체의 타입 안정성을 높이고 형변환의 번거로움이 줄어든다.
```

<br>

### 1️⃣ Generics Class 선언

**일반 클래스**

```java
class Box {
	Object item;

	void setItem(Object item) { this.item = item; }
	Object getItem() { return item; }
}
```

<br>


**Generics Class** 

```java
class Box<B> {
	T item;
	
	void setItem(T item) { this.item = item; }
	T getItem() { return item; }
}
```

- `T` : 타입 변수 (Type variable)
- `E` : 요소 (Element)
- `K` : 키 (Key)
- `V` : 값 (Value)

⇒ 기호의 종류만 다르고 임의의 참조형 타입을 의미하는 것은 모두 같다.

 
<br>


### Generics 용어

```java
class Box<T> {}
```

- `Box<T>`: 제네릭 클래스, T의 Box 또는 T Box라고 읽는다.
- `T` : 타입 변수 또는 타입 매개변수
- `Box` : 원시 타입


<br>


```java
Box<String> b = new Box<String>();
```

- `String` : 매개변수화된 타입
- `new Box<String>()` : 제네릭 타입 호출


<br>


Box<String> 과 Box<Integer> 는 제네릭 클래스 Box<T> 에 서로 다른 타입을 대입하여 호출한 것이고, 별개의 클래스를 의미하는 것이 아님

  
<br>
  
  
### Generics 의 제한

```java
clss Box<T> {
	static T item;           //에러
	static int compare(T t1, T t2) {}        //에러
}
```

→ static 멤버에 타입 변수 T를 사용할 수 없다.

T는 인스턴스 변수로 간주되는데, static멤버는 인스턴스 변수를 참조할 수 없다.

  
<br>
  
  
```java
class Box<T> {
	T[] itemArr;        //OK. T타입의 배열을 위한 참조변수
		
	T[] toArray() {
		T[] tmpArr = new T[itemArr.length];         //에러. 제네릭 배열 생성 불가.

		return tmpArr;
	}
}
```

→ 제네릭 배열 타입의 참조변수를 선언하는 것은 가능하지만, 제네릭 타입의 배열을 생성하는 것도 허용하지 않는다.

→ new 연산자 때문인데, new는 컴파일 시점에 타입 T가 무엇인지 정확하게 알아야 한다.

  
<br>
  
  
### 2️⃣ Generics Class의 객체 생성과 사용

**참조변수와 생성자에 대입된 타입이 일치해야 한다.**

```java
Box<Apple> appleBox = new Box<Apple>();
```

<br>
  
  
두 제네릭 클래스 타입이 상속관계에 있고, 대입된 타입이 같은건 괜찮다.

```java
Box<Apple> appleBox = new FruitBox<Apple>();
```

  
<br>
### 3️⃣ 제한된 제네릭 클래스

```java
FruitBox<Toy> fruitBox = new FruitBox<Toy>();
fruitBox.add(new Toy());         //OK, 과일상자에 장남감을 담을 수 있다.
```

→ 타입 문자로 사용할 타입을 명시하면 한 종류의 타입만 저장할 수 있도록 제한할 수 있지만, 여전히 모든 종류의 타입을 지정할 수 있다.

  
<br>
  
  
**제네릭 타입에 `extends` 를 사용하면 특정 타입의 자손들만 대입할 수 있다.**

```java
class FruitBox<T extends Fruit> {              //fruit의 자손만 타입으로 지정가능
	ArrayList<T> list = new ArrayList<T>();
}
```

  
  <br>
  
  
💬  클래스가 이나라 인터페이스를 구현해야 한다면 `implements` 대신 `extends` 을 사용한다.

```java
interface Eatable {}
class FruitBox<T extends Eatable> {}
```

  
  <br>
  
  
💬  클래스 Fruit의 자손이면서 Eatable 인터페이스도 구현해야 한다면 `&` 기호로 연결한다.
  
  ```java
  class FrutiBox<T extends Fruit & Eatable> {}
  ```

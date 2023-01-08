# Java - switch


### switch는 무엇일까?


경우의 수가 많아지는 경우 기존 ```if``` 문을 사용하면 복잡해지고, 처리시간도 많이 걸린다. <br>
```switch``` 문은 하나의 조건식으로 여러가지의 경우의 수를 처리할 수 있다.


<br>


### switch의 진행 과정

```java
switch (조건식) {
	case value1:
    	System.out.println("value1");
        break;
    case value2:
    	System.out.println("value2");
	case value3:
    	System.out.println("value3");
        break;
    default: 
      	System.out.println("조건을 만족하지 않습니다.")
}
```

1. 조건식 계산
1. 조건식의 결과와 일치하는 case로 이동하여 case문 아래 있는 문장을 수행
3. break나 default를 만나면 빠져나온다.



> break가 없을 경우 다음 break 명령어가 있는 case까지 이어서 수행한다.


<br>


ex) 위에 코드에서는 case가 value2일 때, break 명령어가 없기 때문에 이어서 case value3의 문장도 실행하고 break를 만나고 종료하게 된다.


> default
> 
> 만약에 조건을 만족하는 값이 없다면 default문 아래에 있는 문장을 실행하게 된다.
> 
> * if문의 else와 비슷한 역할을 한다.



* 특별한 경우가 아니라면 각각의 case문마다 break를 써주는게 좋다.


<br>


#### break문을 사용하지 않는 특별한 경우 예시

사용자의 등급을 확인하고, 등급에 맞는 권한을 부여하는 방식


```java
switch (level) {
	case 3:
    	grantDelete();	//삭제 권한
    case 2:
    	grantWrite();   //쓰기 권한
    case 1:
    	grantRead();    //읽기 권한
}
```

등급이 제일 높은 3을 가진 사용자에게는 break문을 사용하지 않음으로 삭제 권한, 쓰기 권한, 읽기 권한을 모두 부여하고 <br>
가장 낮은 등급 1을 가진 사용자에게는 읽기 권한만 부여한다.



<br>




### switch 의 제약조건

switch의 조건식의 결과값은 반드시 정수이어야 한다. 때문에 case의 값 역시 정수이어야 하고 중복되지 않아야 한다. 또한 case의 값은 상수이어야 한다. (변수, 실수는 사용할 수 없다.)

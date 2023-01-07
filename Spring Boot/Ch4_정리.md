### 1️⃣ 빌드 관리 도구
```
💡 JVM이나 WAS가 프로젝트를 인식하고 실행할 수 있게 작성한 소스코드와 프로젝트에 사용된 파일들을 빌드하는 도구
```


<br>


### 2️⃣ 메이븐
```
자바 기반의 프로젝트를 빌드하고 관리하는 도구
```

```pom.xml``` 파일을 작성하여 메이븐 기능을 사용한다.

* pom.xml은 프로젝트, 의존성 라이브러리, 빌드 등의 정보 및 해당 프로젝트를 관리하는 데 필요한 내용이 기술되어 있다


<br>

#### 메이븐의 기능
* 프로젝트 관리 
* 빌드 및 패키징
* 테스트
* 배포


<br>

#### 메이븐의 생명주기

* Default Lifecycle 
  * validate -> compile -> test -> package -> verify -> install -> deploy
* Clean Lifecycle 
  * clean
* Stie Lifecycle
  * site -> site-deploy



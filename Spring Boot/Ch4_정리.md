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




<br>


### 3️⃣ Controller 작성하기

com.example.spring 패키지 아래에 controller으로 하위 패키지를 생성하고 controller 패키지 안에 FirstController(Class)을 생성한다.
```
package com.example.spring.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class FirstController {

    @RequestMapping("/spring")
    public String spring(){
        return "Hello World!";
    }
}
```

<br>


위와 같이 컨트롤러 코드를 작성하고 빌드한다.
그리고 주소창에 localhost:8080/spring을 입력하면

* 스프링부트는 기본 포트가 8080으로 설정되어 있다. 

![스크린샷 2023-01-07 오후 11 32 57](https://user-images.githubusercontent.com/72512101/211157951-db3b178e-c353-41ed-8af2-fd0d747df924.png)






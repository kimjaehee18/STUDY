### 1️⃣ GET API
```
💡 GET API는 웹 애플리케이션 서버에서 값을 가져올 때 사용하는 API이다.
```


<br>


* ```@RestController```은 ```@Controller```에 ```@ResponseBody```가 결합된 어노테이션으로, 클래스에 RestController를 붙이면 하위 메서드에 ```@ResponseBody```를 붙이지 않아도 문자열과 JSON 등을 전송할 수 있다.
* ```@RequesetMapping```은 서버의 URL과 특정 처리를 연동(매핑)시키는 구조이다.

<br>

**RestController과 Controller의 차이점**

* ```@Controller```은 Model객체를 만들어 데이터를 담고 View를 찾지만, ```@RestController```은 단순히 객체만을 반환하고 객체 데이터는 JSON 또는 XML 형식으로 HTTP 응답에 담아서 전송한다.


```
💡REST(Representational State Transfer)란?
  HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고
  HTTP Method(POST, GET, PUT, DELETE, PATCH 등)를 통해
  해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미합니다.
  그리고 이러한 것들을 준수했을 때 그 시스템은 RESTful하다고 한다.
  
  REST의 경우 클라이언트가 특정 URL에 접속하면 웹 페이지를 그리는 것이 아니라 특정 정보 또는 특정 처리 결과를 텍스트 형태로 반환한다.
```


<br>

**예제**

```java
package com.example.spring.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api/v1/get-api")
public class ApiController {
    @RequestMapping(value = "/spring", method = RequestMethod.GET)
    public String getSpring() {
        return "Hello API!";
    }
}
```



<br>

**결과**

![스크린샷 2023-01-08 오전 12 53 24](https://user-images.githubusercontent.com/72512101/211159361-56924aaa-8e99-4924-bc16-01b838763c36.png)

<br>


🚨 스프링4.3 버전 이후로는 @GetMapping, @PostMapping, @PutMapping, @DeleteMapping 을 사용하기 때문에 특별한 경우가 아니면 @RequestMapping을 잘 사용하지 않는다.

<br>


아래 코드는 위의 코드를 @RequestMapping 대신 @GetMapping을 사용하여 구현한 것으로 결과는 위와 똑같다.


```java
package com.example.spring.controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api/v1/get-api")
public class ApiController {

    @GetMapping(value = "/spring")
    public String getSpring2() {
        return "Hello API!";
    }
}
```

<br>


#### @PathVariable
@GetMapping 은 별도의 매개변수 없이 GET API를 구현하는 것이고, 매개변수를 받기 위해서는 URL 자체에 값을 담아 요청하는 방법이 있다.
```@PathVariable``` 을 사용하여 쿼리 형식으로 값을 전달하는 것이 아닌 URL 패스로 파라미터를 전달하여 사용한다.




```java
package com.example.spring.controller;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/get-api")
public class ApiController {

    @GetMapping(value = "/spring/{variable}")
    public String getVariable(@PathVariable String variable) {
        return variable;
    }
}
```

<br>

주소창에 http://localhost:8080/api/v1/get-api/spring/hello 을 입력하면 @GetMapping의 중괄호{} 위치에 매개변수로 hello가 전달되고 화면에 hello가 출력된다. 

![스크린샷 2023-01-08 오전 1 05 00](https://user-images.githubusercontent.com/72512101/211159803-6fb597b8-d1cc-41ce-b272-f06b3fdbaece.png)


<br>




#### @RequestParam

위에서 언급한 ```@PathVariable```은 URL 경로에 값을 담아 요청을 보내는 방법이고, ```@RequestParam```은 쿼리 형식으로 값을 전달하는 것이다.

* 쿼리 형식은 URI에서 '?'를 기준으로 '키=값' 형태로 구성된 요청을 전송하는 방법이다.


<br>


**코드**

```java
package com.example.spring.controller;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/get-api")
public class ApiController {

    @GetMapping(value = "/request")
    public String getRequestParam(@RequestParam String name, @RequestParam String email) {
        return name + " " + email;

    }
}
```

<br>

url에 입력한 것을 보면 '?' 오른쪽으로 '키=값' 형식으로 쿼리스트링이 명시되어 있다. 매개변수를 여러 개 받으려면 '&'를 사용하여 변수 여러 개를 전달 받는다.

<img width="762" alt="스크린샷 2023-01-08 오전 1 18 36" src="https://user-images.githubusercontent.com/72512101/211160364-2ec67003-af58-4d83-9911-df9462c79cee.png">


<br>


### 2️⃣ DTO

```
💡 Data Transfer Object, 각 클래스 및 인터페이스를 호출하면서 전달하는 매개변수로 사용되는 데이터 객체
   다른 레이어 간의 데이터 교환에 활용한다. 
```

<br>


```java
package com.example.spring.dto;

public class MemberDto {
    private String name;
    private String age;
    private String email;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getAge() {
        return age;
    }

    public void setAge(String age) {
        this.age = age;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    @Override
    public String toString() {
        return "MemberDto{" +
                "name='" + name +'\'' +
                ", age='" + age + '\'' +
                ", email='" + email + '\'' + "}";
    }
}
```

<br>

```java
@GetMapping(value = "/request3")
public String getRequestParam3(MemberDto memberDto) {
   return memberDto.toString();
}
```    


<br>


### 3️⃣ POST API
```
💡 저장하고자 하는 리소스나 값을 HTTP 바디에 담아 서버에 전달한다.
```

```@RequestBody```는 HTTP의 Body 내용을 해당 어노테이션이 지정된 객체에 매핑하는 역할을 한다.


<br>


### 4️⃣ PUT API
```
💡 웹 애플리케이션 서버를 통해 데이터베이스 같은 저장소에 존재하는 리소스 값을 업데이트 하는 데 사용한다.
```


<br>


### 5️⃣ 로킹 라이브러리 - Logback
```
💡 로깅(logging) : 애플리케이션이 동작하는 동안 시스템의 상태나 동작 정보를 시간순으로 기록하는 것
```

<br>


자바를 사용하면서 가장 많이 사용되는 로깅 프레임워크는 Logback으로 `Logback`은 log4j 이후에 출시된 로깅 프레임워크로 slf4j를 기반으로 구현되었고, log4j보다 성능이 좋다. <br> 또한 spring-boot-start-web 라이브러리 내부에 내장되어 있어 별도 의존성을 추가하지 않아도 된다.

<br>


Logback을 사용하기 위해서는 리소스 폴더 안에 logback-spring.xml 파일을 생성합니다.


#### logback-spring.xml 살펴보기

**Appender 영역**
```로그의 형태를 설정하고 어떤 방법으로 출력할지 설정하는 곳```
* ConoleAppender : 콘솔에 로그 출력
* FileAppender : 파일에 로그 저장
* RollingFileAppender : 여러 개의 파일을 순회하면서 로그 저장
* SMTPAppender : 메일로 로그 전송
* DBAppender : 데이터베이스에 로그 저장

```xml
<appender name="console" class="ch.qos.logback.core.ConsoleAppender">
    <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
        <level>INFO</level>
    </filter>
    <encoder>                
        <pattern>[%d{yyyy-MM-dd HH:mm:ss.SSS}] [%-5level] [%thread] %logger %msg%n</pattern>
    </encoder>
</appender>

<appender name="INFO_LOG" class="ch.qos.logback.core.rolling.RollingFileAppender">
    <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
        <level>INFO</level>
    </filter>
    <file>${LOG_PATH}/info.log</file>
    <append>true</append>
    <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
        <fileNamePattern>${LOG_PATH}/info_${type}.%d{yyyy-MM-dd}.gz</fileNamePattern>
        <maxHistory>30</maxHistory>
    </rollingPolicy>
    <encoder>
        <pattern>[%d{yyyy-MM-dd HH:mm:ss.SSS}] [%-5level] [%thread] %logger %msg%n</pattern>
    </encoder>
</appender>
```

* `<filter></filter>` : 각 Appender가 어떤 레벨로 로그를 기록하는지 지정한다. <br>
* `<encoder></encoder>` : 로그의 표현 형식을 패턴(pattern)으로 정의한다.

<br>

패턴 예시)

```
<pattern>[%d{yyyy-MM-dd HH:mm:ss.SSS}] [%-5level] [%thread] %logger %msg%n</pattern>
```

* `%d` : 로그 기록 시간
* `%-5level` : 로그 레벨, -5는 출력 고정폭의 값
* `%Logger{length}` : 로거의 이름
* `%thread` : 현재 스레드명
* `%msg(%message)` : 로그 메시지
* `%n` : 줄바꿈

<br>


**Root 영역**

설정 파일에 정의된 Appender를 활용하려면 Root 영역에서 Appender를 참조해서 로깅 레벨을 설정한다.

```xml
<root level="INFO">
    <appender-ref ref="console"/>
    <appender-ref ref="INFO_LOG"/>
</root>
```


<br>


**Logback 적용하기**

Logback은 출력할 메시지를 Appender에게 전달할 Logger 객체를 각 클래스에 정의해서 사용한다.

<br>


* Logger 선언
```java
private final Logger LOGGER = LoggerFactory.getLogger(ApiController.class);
Logger.info("Logback Test");
```

<br>


결과로 콘솔 화면에 로그가 출력된다.

![스크린샷 2023-01-10 오전 12 48 11](https://user-images.githubusercontent.com/72512101/211349274-208540c1-2de5-4a4e-9798-87de8b9cccf9.png)




<br>


**참고**

👉 https://developer.mozilla.org/ko/docs/Glossary/REST

👉 https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80

👉 https://dorothy-koo.gitbooks.io/springboot/content/chapter1.html

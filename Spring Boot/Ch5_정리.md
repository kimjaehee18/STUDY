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



```
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


**참고**

👉 https://developer.mozilla.org/ko/docs/Glossary/REST

👉 https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80

👉 https://dorothy-koo.gitbooks.io/springboot/content/chapter1.html

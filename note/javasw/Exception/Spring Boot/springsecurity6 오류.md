### 날짜 : 2024-01-10 14:52

___

### 주제 : #제텔카스텐

___

### Spring security 빌드 : 

Thymeleaf와 security을 build.gradle 코드를 가져오게 될 경우
``` java
implementation 'org.thymeleaf.extras:thymeleaf-extras-springsecurity6'
```

위의 코드만 들어가게 됩니다.
아래의 코드를 1개더 추가해서 누락된 코드가 없도록 해야 합니다.

``` java
implementation 'org.springframework.boot:spring-boot-starter-security'  
implementation 'org.thymeleaf.extras:thymeleaf-extras-springsecurity6'
```

+) 뭔가 빌드에서 컴파일 오류나서 `thymeleaf-extras-springsecurity5`로 바꿈

___

### 출처(참고문헌)

- [Thymeleaf 사용하는 프로젝트에서 Spring security 빌드할 때 주의할 점](https://velog.io/@minjung0/JavaSpringBoot-Thymeleaf-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90%EC%84%9C-Spring-security-%EB%B9%8C%EB%93%9C%ED%95%A0-%EB%95%8C-%EC%A3%BC%EC%9D%98%ED%95%A0-%EC%A0%90)

___

### 연결문서

- [[Spring Boot 생성]]
- [[Spring Boot Setting]]

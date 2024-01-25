### 날짜 : 2024-01-15 16:56

___

### 주제 : #security #password

___

### 문제 : 

![[Pasted image 20240115165609.png]]

``` java
Using generated security password: ???

This generated password is for development use only. Your security configuration must be updated before running your application in production.
```

>[!note] 번역
>
> 생성된 보안 비밀번호 사용 : 
> 생성된 비밀번호는 개발용으로만 사용됩니다. 
> 프로덕션 환경에서 애플리케이션을 실행하기 전에 보안 구성을 업데이트해야 합니다.

### 원인 :

> Security가 AutoConfiguration 되면서 생성됩니다.
> @ConditionalOnMissingBean 를 살펴보면 3개의 클래스가 걸려있지 않는다면 이것이 활성화 됩니다.
> - AuthenticationManager.class
> - AuthenticationProvider.class
> - UserDetailsService.class
> 
> Security를 쓴다는건 인증을 허가하는 부분이 있어야 하는데 위의 3개는 그것을 하는 클래스다. 그런데 이것들이 비어있다보니 비밀번호를 자동 생성하여 로그에 찍힌 것이다.

### 해결방안 : 

> application.properties에서 
> ``` java
> spring.security.user.password=패스워드
> ```
> 추가 하면 됩니다.

___

### 출처(참고문헌)

- [Using generated security password 가 보일 때](https://lemontia.tistory.com/1035)

___

### 연결문서

- [[Spring Boot 생성]]
- [[Spring Boot Setting]]


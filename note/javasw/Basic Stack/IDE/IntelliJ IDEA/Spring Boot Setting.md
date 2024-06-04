### 주제 : #SpringBoot #Setting

___

### 메모 : 

```java
# 서버 포트  
server.port=8181  
# 세션 소멸 시간 설정  
server.servlet.session.timeout=1h
# jasypt  
jasypt.encryptor.password=mySecretPassword  
# 한글 깨짐 방지  
server.servlet.encoding.force-response=true  

# 접두사 / 접미사  
# SpringBoot"에서 /static/ 디렉토리는 기본적으로 정적 자원(Static Resources)을 제공하기 위한 디렉토리입니다. (접두사 지정하지 않아도 됩니다.)(단, 다른 디렉토리는 해야함.)  
# spring.mvc.view.prefix=classpath:/resources/\**
# spring.mvc.view.prefix=/resources/\**
spring.mvc.view.suffix=.html  

# /static/로 시작하는 요청 경로를 정적 리소스로 처리합니다.  
spring.mvc.static-path-pattern=/static/\**

# OSIV"가 TRUE"의 장점 : 사용자에게 응답 또는 view"가 렌더링 될 때까지 영속성컨텍스트를 유지한다.  
# 단점 : 실시간 트래픽이 중요한 어플리케이션에서는 DB Connection"이 모자를 수 있다.  
spring.jpa.open-in-view=false  
# Using generated security password 에러 해결방법  
spring.security.user.password=kjayvam  
  
# MariaDB 데이터베이스의 URL 주소  
spring.datasource.url=jdbc:mariadb://localhost:3306/planner  
# MariaDB 데이터베이스에 접속할 때 사용할 사용자 이름  
spring.datasource.username=root  
# MariaDB 데이터베이스에 접속할 때 사용할 비밀번호  
spring.datasource.password=mariadb  
# MariaDB JDBC 드라이버의 클래스 이름  
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver
```
![[Pasted image 20230812114321.png]]

___

### 출처(참고문헌)

___

### 연결문서

- [[0.Spring Boot]]
- [[0.IntelliJ]]


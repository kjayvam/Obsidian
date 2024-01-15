### 주제 : #DataSource #URL #Error

___

### 문제 : 

![[Pasted image 20230812125603.png]]

```
Action:

Consider the following:
	If you want an embedded database (H2, HSQL or Derby), please put it on the classpath.
	If you have database settings to be loaded from a particular profile you may need to activate it (no profiles are currently active).
```

>[!note] 번역
>
> 임베디드 데이터베이스(H2, HSQL, Derby)를 원하시면 클래스패스에 넣어주세요.
> 로드할 데이터베이스 설정이 있는 경우 이를 활성화해야 할 수도 있습니다

### 원인 1 : 

> DataSource 설정이 제대로 되어 있지 않아서 생긴 문제이다.
> Spring Boot 에서는 DataSource 를 필요로 하는 아래 같은 의존성이 추가만 되어 있어도
> 자동으로 DataSource 생성을 시도하기 때문이다.

```
org.springframework.boot:spring-boot-starter-data-jpa
org.mybatis.spring.boot:mybatis-spring-boot-starter
```

### 해결방안 1 : 

build.gradle 파일에 `com.h2database:h2` 의존성이 제대로 추가되었는지 확인해주세요.

```
dependencies {
//	implementation 'com.h2database:h2'  
//	runtimeOnly 'com.h2database:h2'
}
```

> 2개 중 하나만 의존성을 추가하면 된다.

### 원인 2 : 

> JPA는 객체와 데이터베이스 간 매핑을 자동 처리하는 자바 표준 기술 입니다.
> 테스트와 메인에서 모두 사용 가능합니다.
> 개발자의 생산성을 높이며, 다양한 데이터베이스에 대응하고, 테스트의 안정성을 증진시키고 데이터베이스에 대한 연동을 용이하게 함입니다.

> 나 같은 경우, JPA를 생성을 하였기 때문에 생긴 문제로 보여진다.
> JPA는 기본적으로 DB와 연결이 되어 있어야 합니다.
> 연결이 되어 있지 않기 때문에 생긴 문제입니다.

### 해결방안 2 : 

> resources 안에 application.properties를 클릭

```
# MariaDB JDBC 드라이버의 클래스 이름
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver  
# MariaDB 데이터베이스에 접속할 때 사용할 사용자 이름
spring.datasource.username=root  
# MariaDB 데이터베이스에 접속할 때 사용할 비밀번호
spring.datasource.password=mariadb  
# 데이터베이스의 URL 주소
spring.datasource.url=jdbc:mysql://localhost:3306/planner
```

___

### 출처(참고문헌)

- [dataSource 해결방법](https://findmypiece.tistory.com/61)
- [프로젝트 생성](https://www.youtube.com/watch?v=6CJ6akFElPc&list=PLZzruF3-_clsWF2aULPsUPomgolJ-idGJ&index=5)


___

### 연결문서

- [[Spring Boot 생성]]
- [[Spring Boot Setting]]


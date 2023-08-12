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

### 원인 : 

> DataSource 설정이 제대로 되어 있지 않아서 생긴 문제이다.
> Spring Boot 에서는 DataSource 를 필요로 하는 아래 같은 의존성이 추가만 되어 있어도
> 자동으로 DataSource 생성을 시도하기 때문이다.

```
org.springframework.boot:spring-boot-starter-data-jpa
org.mybatis.spring.boot:mybatis-spring-boot-starter
```

> 나 같은 경우, JPA를 생성을 하였기 때문에 생긴 문제로 보여진다.

### 해결방안 : 

build.gradle 파일에 `com.h2database:h2` 의존성이 제대로 추가되었는지 확인해주세요.

```
dependencies {
//	implementation 'com.h2database:h2'  
//	runtimeOnly 'com.h2database:h2'
}
```

> 2개 중 하나만 의존성을 추가하면 된다.

___

### 출처(참고문헌)

- [dataSource 해결방법](https://findmypiece.tistory.com/61)

___

### 연결문서

- [[Spring Boot 생성]]


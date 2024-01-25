### 날짜 : 2024-01-17 15:25

___

### 주제 : #class #file #version

___

### 문제 : 

![[Pasted image 20240117152521.png]]

```java
2024-01-17 15:21:32.050 ERROR 12676 --- [nio-8181-exec-3] o.a.c.c.C.[.[.[/].[dispatcherServlet]    : Servlet.service() for servlet [dispatcherServlet] in context with path [] threw exception [Handler dispatch failed; nested exception is java.lang.ExceptionInInitializerError] with root cause

java.lang.UnsupportedClassVersionError: org/hibernate/proxy/HibernateProxy has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0
```

>[!note] 번역
> 
> dispatcherServlet에 대한 에러가 발생했습니다.
> 
> 사용하고 있는 것은 Java 8 이하(클래스 파일 버전 52) 입니다.
> 로딩하려는 클래스 파일은 Java 11 이상(클래스 파일 버전 55)입니다.

### 원인 : 

> 1. 호환되는 java 버전과 hibernate의 버전이 다르기 때문에 생기는 문제이다.

> 2. build.gradle에서 JPA를 가져올 때 hibernate를 같이 가져오는데 
> 이때, `implementation "org.hibernate.orm:hibernate-core:{version}"`을 가져오게 된다

>[!note] 차이점
>
> ``` java
> implementation "org.hibernate.orm:hibernate-core:{version}"
> implementation 'org.hibernate:hibernate-core:{version}'
> ```
> 
> " " 
> 
> - 따옴표로 묶인 문법
> - 의존성 버전을 지정하지 않음
> - 최신 버전 자동 다운로드
> 
> ' '
> 
> - 싱글쿼테이션으로 묶인 문법
> - 따옴표가 아닌 싱글쿼테이션 사용
> - 의존성 버전 지정 가능

### 해결 : 

> [hibernate 공식사이트](https://hibernate.org/orm/releases/)에서 호환되는 java 버전을 확인하고 좌표를 가져와야 합니다.
> 
> 버전을 최신버전으로 업데이트 되지 않도록 " "사용하는 문법보다는 ' '를 사용하는 문법을 사용하는 것이 좋습니다.

>[!note] 해결방법 (버전을 작성해야 합니다.)
>
> 수정 전 `build.gradle`
> 참고로 `' ' (싱글쿼테이션)`사이에는 띄어쓰기를 하면 안됩니다.
> 
> ``` 
> implementation "org.hibernate.orm:hibernate-core:6.4.1.Final" 
> ```
> 
> 수정 후 `build.gradle`
> 
> ```
> implementation 'org.hibernate:hibernate-core:5.6.15.Final'
> ```

___

### 출처(참고문헌)

- [](https://stackoverflow.com/questions/43603040/java-lang-noclassdeffounderror-org-hibernate-proxy-hibernateproxy-which-jar-i)
- [잘못된 Java 릴리스 버전으로 생성 된 최대 절전 모드 프록시 클래스](https://github.com/quarkusio/quarkus/issues/13871)


___

### 연결문서

- [[Spring Boot 생성]]


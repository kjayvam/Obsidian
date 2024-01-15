### 날짜 : 2024-01-15 15:23

___

### 주제 : #context

___

### 문제 1 : 

![[Pasted image 20240115152327.png]]

```
Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'dataSourceScriptDatabaseInitializer' defined in class path resource [org/springframework/boot/autoconfigure/sql/init/DataSourceInitializationConfiguration.class]: Unsatisfied dependency expressed through method 'dataSourceScriptDatabaseInitializer' parameter 0; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'dataSource' defined in class path resource [org/springframework/boot/autoconfigure/jdbc/DataSourceConfiguration$Hikari.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [com.zaxxer.hikari.HikariDataSource]: Factory method 'dataSource' threw exception; nested exception is org.springframework.boot.autoconfigure.jdbc.DataSourceProperties$DataSourceBeanCreationException: Failed to determine a suitable driver class
```

>[!note] 번역
>
> 컨텍스트 초기화 중 예외 발생 - 새로 고침 시도 취소 :
> 'dataSourceScriptDatabaseInitializer'인 Bean을 생성하는 중 오류가 발생했습니다.
> dataSource'인 Bean을 생성하는 중 오류가 발생했습니다.
> 적합한 드라이버 클래스를 결정하지 못했습니다.

### 문제 2 : 

![[Pasted image 20240115161434.png]]
```
Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'entityManagerFactory' defined in class path resource [org/springframework/boot/autoconfigure/orm/jpa/HibernateJpaConfiguration.class]: Bean instantiation via factory method failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean]: Factory method 'entityManagerFactory' threw exception; nested exception is com.zaxxer.hikari.pool.HikariPool$PoolInitializationException: Failed to initialize pool: null
```

>[!note] 번역
>
> 컨텍스트 초기화 중 예외 발생 - 새로 고침 시도 취소 :
> 'entityManagerFactory'인 Bean을 생성하는 중 오류가 발생했습니다.
> 팩토리 메서드를 통한 Bean 인스턴스화에 실패했습니다.
> 풀을 초기화하지 못했습니다. null

### 원인 1 : 

> 이 오류는 Spring Boot가 HikariDataSource를 생성할 때 드라이버 클래스를 찾을 수 없어서 발생합니다.

### 원인 2 : 

> 이 오류는 HikariCP에서 발생한 것입니다.
> HikariCP는 Spring Boot에서 JPA를 사용할 때 사용하는 데이터베이스 커넥션 풀입니다.
> HikariCP는 데이터베이스 커넥션을 관리하고, 데이터베이스 커넥션이 부족할 때 자동으로 새로운 커넥션을 생성합니다.
> 하지만, HikariCP가 데이터베이스 커넥션을 생성하지 못하면 이 오류가 발생합니다.

### 해결방안 1 : 

- spring.datasource.driver-class-name : 드라이버 클래스 이름이 올바른지 확인합니다.
- spring.datasource.url : 데이터베이스 URL이 올바른지 확인합니다.
- spring.datasource.username : 데이터베이스 사용자 이름이 올바른지 확인합니다.
- spring.datasource.password : 데이터베이스 비밀번호가 올바른지 확인합니다.

> 이 설정들을 확인해도 오류가 해결되지 않으면, Spring Boot 버전이 너무 낮거나, HikariCP 버전이 너무 낮은 경우일 수 있습니다.

### 해결방안 2 : 

- 데이터베이스가 정상적으로 실행되고 있는지 확인합니다.
- 데이터베이스 서버가 포트 3306에서 수신 대기하고 있는지 확인합니다.
- 데이터베이스 사용자 이름과 비밀번호가 올바른지 확인합니다.
- 데이터베이스 스키마가 올바른지 확인합니다.
- HikariCP의 설정이 올바른지 확인합니다.

> `application.properties` 파일에서
> ```
> dependencies {
> 	implementation "org.hibernate.orm:hibernate-core:6.4.1.Final"
> }
> 또는
> ext["hibernate.version"] = "5.6.5.Final" 추가
> ```

> [Hibernate-JPA의 버전 별 호환 및 자료](https://hibernate.org/orm/releases/)
> 
> ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbi9yHC%2FbtrzHNe2k7F%2F43P52d5JYS738tkb08KVIk%2Fimg.png)
> 
> Java 및 JPA를 알

___

### 출처(참고문헌)

- [hibernate 버전](https://www.inflearn.com/questions/688953/hibernate-%EB%B2%84%EC%A0%84)
- [호환되는 버전 찾기](https://ajdahrdl.tistory.com/218)

___

### 연결문서

- [[Spring Boot 생성]]
- [[Spring Boot Setting]]


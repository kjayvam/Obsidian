### 날짜 : 2024-01-15 14:11

___

### 주제 : #Driver #Connetcor

___

### 문제 : 

> mariaDB를 이용해서 JPA와 연결하는 도중에 발생한 에러

![[Pasted image 20240115141343.png]]

![[Pasted image 20240115141154.png]]

### 원인 :

> 콘솔창에 'jdbcUrl, jdbc:mysql:localhost:3306planner를 허용하지 않는다고 주장합니다.'의 에러가 발생
> 즉, mariaDB가 프로젝트와 연결이 안되기 때문에 발생

### 해결방안 :

[MariaDB 커넥터](https://mariadb.com/kb/en/about-mariadb-connector-j/)에서 다운로드

> 설치도 안 했는데 해결이 되었다??
> 머지???

___

### 출처(참고문헌)

- [org.mariadb.jdbc.Driver 오류 해결법](https://leirbag.tistory.com/48)
- [IntelliJ-JDBC-MariaDB연결하기(JDBC)](https://zer0lab.tistory.com/18)

___

### 연결문서

- [[Spring Boot 생성]]
- [[Spring Boot Setting]]


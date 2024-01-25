### 날짜 : 2024-01-17 16:07

___

### 주제 : #JMX #service #URL  #에러

___

### 문제 : 

> IntelliJ를 사용하여 Sprint Boot를 실습하던 중 앱 실행 시 접근은 가능하나 에러로그 발생하여 확인해 보았다.

![[Pasted image 20240117160708.png]]

### 원인 :

검색 된 원인은 2018.3.4 IntelliJ IDEA부터 Spring Boot 로컬 JMX 커넥터를 사용합니다.  
로컬 JMX 모니터링에는 몇 가지 제한 사항이 있고, Spring Boot 애플리케이션과 IntelliJ IDEA JVM의 비트 수가 다른 경우 로컬 JMX 커넥터 주소를 가져올 수 없다.  
동일한 비트 수로 JVM에서 애플리케이션을 실행할 수 없는 경우 문제를 해결하기 위해 Spring Boot 실행 구성의 VM 옵션에 다음을 추가할 수 있다.

### 해결방안 1 : 

1. IntelliJ 상단 Run 메뉴 선택
2. Edit Configurations... 선택
3. VM options 추가
> ```
> -Dcom.sun.management.jmxremote.port={some_port/앱 포트와 다른 포트} -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
> ```

### 해결방안 2 : 

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FHJKBb%2FbtrLVX4oRdJ%2Fm6LKDv298k6kqunoJTDIrK%2Fimg.png)

> `Disable JMX agent`(JMX 비활성화)를 체크

___

### 출처(참고문헌)

- [IntelliJ “Failed to retrieve application JMX service URL” 에러](https://velog.io/@flasharrow/IntelliJ-Failed-to-retrieve-application-JMX-service-URL-%EC%97%90%EB%9F%AC)
- [Intellij Spring boot Jmx RMI remote objects have benn exported](https://devhj.tistory.com/22)

___

### 연결문서

- [[0.내부링크]]


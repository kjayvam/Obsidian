### 주제 : #SpringBoot #첫실행시오류

___

### 문제  : 

![[Pasted image 20230812111228.png]]

```
no matching variant of org.springframework.boot:spring-boot-gradle-plugin:3.1.2 was found.

the consumer was configured to find a library for use during runtime, compatible with java 8, packaged as a jar, and its dependencies declared externally, as well as attribute 'org.grale.plugin.api-version' with value '8.2.1' but:
```

### 원인 : 

> java 8 버전은 오래된 버전이기 때문에 spring boot 3.x.x 버전은 지원을 안 한다.
> spring boot 2.x.x 버전으로 사용해야 한다.

### 해결 방안 : 

1. java의 낮은 버전에 맞출 경우 : version 2.xx 버전으로 변경하거나 새로 시작하여 버전을 낮춘다.
2. 스프링부트 버전에 맞출 경우 : java 버전을 올린다.

![[Pasted image 20230812113257.png]]
![[Pasted image 20230812112629.png]]
### 결과 : 
![[Pasted image 20230812112938.png]]

___

### 출처(참고문헌)

___

### 연결문서

- [[Spring Boot 생성]]
- [[Spring Boot Setting]]

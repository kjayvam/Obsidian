### 날짜 : 2024-01-15 16:38

___

### 주제 : #template #Thymeleaf #find

___

### 문제 : 

![[Pasted image 20240115163901.png]]

```
Cannot find template location: classpath:/templates/ (please add some templates, check your Thymeleaf configuration, or set spring.thymeleaf.check-template-location=false)
```

>[!note] 번역
> 
> 템플릿 위치를 찾을 수 없습니다 :
> 템플릿을 추가하거나 Thymeleaf 구성을 확인하세요.

### 원인 : 

> resources > templates에 아무것도 없기 때문에 발생하는 에러 입니다.

### 해결방안 : 

> resources > templates에 아무거나 넣어두면 해결이 됩니다.

___

### 출처(참고문헌)

- [thymeleaf 에러](https://www.inflearn.com/questions/298965/%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94-thymeleaf-%EC%97%90%EB%9F%AC-%EC%A7%88%EB%AC%B8%EC%9E%85%EB%8B%88%EB%8B%A4)

___

### 연결문서

- [[Spring Boot 생성]]


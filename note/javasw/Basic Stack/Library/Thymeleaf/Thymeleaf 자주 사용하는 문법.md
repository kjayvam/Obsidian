### 날짜 : 2024-01-30 16:12

___

### 주제 : #Thymeleaf #자주사용

___

### 문법 : 

>[!note] th:text
>
> 문자열 생성
>
> ``` java
> th:text=" ${이름} "
> ```

>[!note] th:each
> 
> 반복문
> 
> ``` java
> th:each="article : ${articleList}"
> ```

>[!note] th:if
> 
> if 조건문
> 
> ``` java
> th:if=${data != null}
> ```

>[!note] th:href
> 
> 이동 경로
> 
> ``` java
> th:href=" @{/article/list(id= ${data} )} "
> ```

### 예제 :

>[!note] th:each
> 
> 반복 출력
>
> ``` html
> <tr th:each="item: ${items}">  
> 	<td th:text="${item.price}">100</td>  
> </tr>
> ```

___

### 출처(참고문헌)

- [thymeleaf(공식페이지)](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#standard-expression-syntax)
- [STUDY AND LESSON(tistory.com)](https://developer-rooney.tistory.com/category/Java%20Web/Thymeleaf)

___

### 연결문서

- [[0.Thymeleaf]]

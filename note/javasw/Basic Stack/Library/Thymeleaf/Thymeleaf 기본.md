### 날짜 : 2024-01-30 15:33

___

### 주제 : #Thymeleaf #기본
___

### 기본 : 

>[!note] @import
>
> ``` html
> <html xmlns:th="http://www.thymeleaf.org">
> ```

>[!note] 타임리프 사용법
> 
> java : 컨트롤러에서 Model을 통해 'name'이란 이름에 value를 넣어 View 부분으로 보냅니다.
> 
> ``` java
> @RequestMapping("/#") 
> public class ArticleController {
>  
> 	@GetMapping("/#") 
> 	public String articleList(Model model) { 
> 	
> 		model.addAttribute("키", value); 
> 		return "article/list"; 
> 	} 
> }
> ```
> 
> html : JSP처럼 서버에서 받아온 데이터를 ${ } 을 이용하여 표기합니다.
> 
> ``` html
> th:text="${키}"
> ```

### 표현식

>[!note] @{ ... } 
>
> URL 링크 표현식
> 
> ``` html 
> th:href="@{/css/bootstrap.min.css}"  
> th:href="@{/{itemId}/edit(itemId=${item.id})}"
> ```

>[!note] \${ ... }
> 
> 변수
>
> ``` html
> th:text=${user.name}
> ```

>[!note] *{ ... }
> 
> 선택 변수
>
> ``` html
> <tr th:object="${items}">  
> 	<td th:text="*{price}">100</td>  
> </tr>
> ```

>[!note] #{ ... }
> 
> 메시지. properties 같은 외부 자원에서 코드에 해당하는 문자열 get.
>
> ``` html
> th:text="#{member.register}"
> ```

>[!note] ~{ ... }
>
> fragment를 참조합니다.
> 조각 표현
> 경로가 단순하면 생략이 가능합니다.
>
>```html
> <footer th:fragment="copy"> 푸터 자리 입니다. </footer> 
> <footer th:fragment="copyParam (param1, param2)"> 
> 	<p>파라미터 자리 입니다.</p> 
> 	<p th:text="${param1}"></p> 
> 	<p th:text="${param2}"></p> 
> </footer>
>```
>
> ``` html
> <div th:insert="~{template/fragment/footer :: copy}"></div>
> <div th:insert="template/fragment/footer :: copy"></div> 
> <div th:replace="~{template/fragment/footer :: copy}"></div> 
> <div th:replace="template/fragment/footer :: copy"></div> 
> <div th:replace="~{template/fragment/footer :: copyParam ('데이터1', '데이터 2')}"></div>
> ```


>[!note] \| ... \|
> 
> 리터럴 대체
>
> ``` html
> th:text="|Hi ${user.name}!|"  
> (= th:text="'Hi '+${user.name}+'!'"
> ```
> 
> ```java
> <span th:text="'welcome to our application, ' + ${user.name} + '!' ">  
> <span th:text="|welcome to our application, ${user.name}!|">  
> ```
> 
> ```html
> th:onclick="'location.href=' + '\'' + @{/basic/items/add} + '\''"  
> th:onclick="|location.href='@{/basic/items/add}'|"
> ```

### 조건 연산 : 

>[!note] if
>
> - if-then : (if) ? (then)
> - if-then-else : (if) ? (then) : (else)
> - Default : (value) ?: (defaultValue)

___

### 출처(참고문헌)

- [thymeleaf(공식페이지)](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#standard-expression-syntax)
- [[Thymeleaf] 타임리프란? (+기본적인 사용법)](https://yeonyeon.tistory.com/153)
- [STUDY AND LESSON(tistory.com)](https://developer-rooney.tistory.com/category/Java%20Web/Thymeleaf)

___

### 연결문서

- [[0.Thymeleaf]]


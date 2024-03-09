### 날짜 : 2024-01-30 16:22

___

### 주제 : #Thymeleaf #js #message #URL 

___

### 방법 : 

>[!note] 문법
>
> ``` java
> @Controller 
> public class HomeController { 
> 	
> 	@GetMapping("/test") 
> 	public String test(Model model) { 
> 		
> 		model.addAttribute("message", "정상적으로 처리되었습니다."); 
> 		model.addAttribute("searchUrl", "https://www.google.com"); 
> 		return "test"; 
> 	} 
> }
> 
> ```
> 
> ``` html
> <script th:inline="javascript">
> 
> /*<![CDATA[*/
> 
> // 이 사이에 자바스크립트 코드를 적어주고 컨트롤러에서 넘어온 변수는 [[ ${   } ]] 로 감싸줍니다.
> 
> /*]]>*/
> 
> </scrirpt>
> ```
> 

>[!note] 참고 예제
>
> ``` html
> <script th:inline="javascript"> 
> 
> /*<![CDATA[*/ 
> 
> var message = [[${message}]]; 
> alert(message); 
> 
> location.replace([[${searchUrl}]]); 
> 
> /*]]>*/ 
> 
> </script>
> ```
> 
> ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmNXIc%2FbtrhQYqYPjQ%2FoqNv9LBvRWGn5nM2Hx1jek%2Fimg.png)
> 
> 위 메시지를 띄운 후 구글로 이동하게 됩니다.

### 주의 : 

타임리프 3.0 버전부터는 스크립트 사용 시 CDATA 구문을 작성하지 않아도 됩니다. 
[타임리프 공식 문서](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html)

___

### 출처(참고문헌)

- [네이버](naver.com)

___

### 연결문서

- [[0.내부링크]]


### 날짜 : 2024-01-30 16:16

___

### 주제 : #Thymeleaf #a태그 #링크

___

### 방법 : 

>[!note] 콜아웃
>
> ``` html
> <!-- 특정 url로 이동 --> 
> <a th:href="@{https://developer-rooney.tistory.com}">글 상세보기</a> 
> 
> <!-- 현재 서버 내에서 이동 --> 
> <a th:href="@{/board/list}">게시글 리스트</a> 
> 
> <!-- 파라미터를 넘길 시 --> 
> <a th:href="@{/board/view(id = ${board.id})}">글 상세보기</a> 
> 
> <!-- 파라미터를 여러 개 넘길 시 --> 
> <a th:href="@{/board/view(id = ${board.id}, writer = ${board.writer}})}">글 상세보기</a> 
> 
> <!-- PathVariable 사용 시 --> 
> <a th:href="@{/board/view/{id}(id = ${board.id})}">글 상세보기</a>
> ```

___

### 출처(참고문헌)

- [thymeleaf(공식페이지)](https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#standard-expression-syntax)
- [STUDY AND LESSON(tistory.com)](https://developer-rooney.tistory.com/category/Java%20Web/Thymeleaf)

___

### 연결문서

- [[0.Thymeleaf]]


### 날짜 : 2024-03-14 02:44

___

### 주제 : #Merge #병합

___

### 설명 : 

> branch에서 main의 변경사항을 가져올 때

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FzhUON%2FbtrxB44BqqC%2FRtLIOWMBGj7PtRcQByzT3k%2Fimg.png)

> 병합을 위해 merge into New 버튼을 눌러줍니다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FQZ7C0%2FbtrxoHa4z3w%2Fh1BDxz3F27MuDvYzgi1Kw1%2Fimg.png)

> 작업했던 브런치에서 main 브런치와 병합할 것이기 때문에 main을 눌러준 뒤 ,
> Create a merge Commit 버튼을 눌러줍니다.

>[!note] Create a Merge Commit (Merge)
>
> a, b, c 를 refer 하는 m 커밋 노드 생성, m은 parent로 Init, c 를 가짐
>
> ![](https://image.toast.com/aaaadh/real/2017/techblog/Screen%20Shot%2020170529%20at%2012.15.48%20PM.png)


>[!note] Squash and Merge
>
> - a, b, c 를 합쳐서 새로운 커밋으로 만들고, 머지 대상 브렌치에 추가, 'a,b,c' 커밋은 parent를 Init 하나만 가짐.
>
> ![](https://image.toast.com/aaaadh/real/2017/techblog/Screen%20Shot%2020170529%20at%2012.15.51%20PM.png)

>[!note] Rebase and Merge
>
> a, b, c 를 심리스하게 머지 대상 브렌치로 추가, 각 커밋들은 모두 parent를 하나씩만 가짐.
> 
> ![](https://image.toast.com/aaaadh/real/2017/techblog/Screen%20Shot%2020170529%20at%2012.15.55%20PM.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FxFAL7%2Fbtrxr5bC75p%2Fk37PKpy0QwOUoA9JxZ6IhK%2Fimg.png)

> main과, 내가 수정한 파일과 충돌(Conflict)이 있으면 다음과 같은 팝업이 나옵니다.
> 이를 수정해주기 위해 vscode로 이동해줍니다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FO8p5L%2FbtrxAbCXh5N%2FvJ70Y3jkYK4946dWGqpCKk%2Fimg.png)

> 내가 수정한 파일과 main의 파일이 충돌이 되면, vscode에 다음과 같이 표시됩니다.
> 초록색으로 표시된 영역이 내가 수정한 영역(Currnet change),
> 파란색으로 표시된 영역이 main의 영역입니다.

>[!note] 빨간색으로 표시한 영역으로 충돌(Conflict)을 어떻게 처리할 지 선택할 수 있습니다.
>
> 1. Accept Current Change -> 헤드 부분을 적용  
> 2. Accept Incoming Change -> 변경된 부분을 적용(병합 대상이 된 브랜치의 내용으로 변경)  
> 3. Accept Both Change -> 둘다 적용(말그대로 헤드와 변경된 부분 둘다 남겨준다.)  
> 4. Compare Change -> 컨플릭트가 난 부분을 좀 더 보기쉽게 보여준다.

>[!note] Conflict가 일어날 때 헷갈리는 점
>
> Use the modified file from main : 기본 브랜치(main)에서 수정된 파일을 사용 
> Use the modified file from branch : 본인이 작업하던 프로젝트를 사용
>
> ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fywmdr%2FbtrK2tcmddI%2FBxrendOoaRhu4Dn52ssPW0%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbwTW0s%2FbtrxHXDnFxi%2Fsk7d8xN9j7o4gPaaGJWNU0%2Fimg.png)

> 충돌(Confilcts)해결, 병합완료 팝업입니다.
> 아래의 merge버튼을 누른 뒤, push 해주면 됩니다.

___

### 출처(참고문헌)

- [깃허브 데스크탑 협업 사용법](https://eunyoe.tistory.com/210)

___

### 연결문서

- [[0.GitHub Desktop]]


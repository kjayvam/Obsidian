### 날짜 : 2024-01-15 11:46

___

### 주제 : #오라클 #Oracle #Port #SID

___

### 접속 :

> 1. 명령 프롬포트(CMD)를 오픈
> 2. 아래 명령어를 통해 Oracle DB에 접속
>  ```
>  sqlplus system/비밀번호
>  ```

### Port 번호, SID 조회

>[!note] SID 조회
> ```
> select name from v$database;
> ```

>[!note] Port 조회
> ```
> select dbms_xdb.gethttpport() from dual;
> ```

>[!note] Port 변경 명령어
> ```
> exec dbms_xdb.sethttpport(변경할포트번호);
> ```

___

### 출처(참고문헌)

- [오라클 Port 번호 및 SID 확인 방법](https://backendcode.tistory.com/294)

___

### 연결문서

- [[0.내부링크]]


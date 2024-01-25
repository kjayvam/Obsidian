### 날짜 : 2024-01-15 10:01

___

### 주제 : #MariaDB #설치

___

### MariaDB 다운로드 : 

![[Pasted image 20240115100503.png]]

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbdfaKz%2FbtrYYpmsgJ5%2FELTCezpdTfw05Bv1FFXDc1%2Fimg.png)

> Alpha,  RC는 개발 버전
> Alpha는 개발 초기단계의 버전
> RC는 출시 직전의 버전
> Alpha,  RC를 제외한 최신 버전을 설치하기

### MariaDB 설치

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb5Kfqw%2FbtrY2nPmbmm%2FCcKDgw7zIvtOZLxbeAo2e1%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FGzvl3%2FbtrYUTInNg9%2FmdW4MWK5qEXCuoSEyM2de0%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbyr5ZJ%2FbtrYT8Z5iua%2Fmb9v7ag9qZqKezjv1lJlYK%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcK8r70%2FbtrYT9koaeE%2F4n7rlbdn6mfGN1GAOnsR11%2Fimg.png)

> 비밀번호 : mariadb

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FYR8T0%2FbtrY1mXiRaJ%2FYCC0NHgk61Ok5FLTGHYDF0%2Fimg.png)

> MySQL에 작성한 것이 있다면 따라하기

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FO6ltX%2FbtrYTNIHjw3%2FeURmLftT2WNM0meyisonl0%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbOcKvg%2FbtrYT8TnvqJ%2FwW9SN7WhfUKhcJWMEP92x0%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fd20WUP%2FbtrYUajj5tM%2Fb6EDERNNNNfMxurXglfvv0%2Fimg.png)

> 시작메뉴에 설치된 것을 확인
> HeidiSQL는 MariaDB와 함께 설치되는 DBMS 관리 툴(프로그램)입니다.
> HeidiSQL를 대신해서 사용하는 프로그램이 있다면 삭제해도 됩니다.
> [디비버(DBeaver)](https://dbeaver.io/download/), [인텔리제이(IntelliJ)](https://www.jetbrains.com/ko-kr/idea/), [MySQL Workbench](https://dev.mysql.com/downloads/workbench/) 사용 가능

### MariaDB 환경 변수 설정

> 1. 내 PC > 시스템 속성 > 고급 시스템 설정 > 환경변수
> 2. 시스템 변수 > Path 선택 > 편집 선택

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdGZNez%2Fbtq8Or9CAV0%2F3av6qBvPVioE5YQkZ40kD0%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcxLKqF%2Fbtq8IEQCNrT%2FSINgBdl3QbCmfKdgwpKc9k%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbLAKhv%2Fbtq8GQjfksp%2FPVq30GoCGv2KMBRXdzyivK%2Fimg.png)

> MariaDB의 bin 경로 붙여넣기

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcPfPS7%2Fbtq8HHF54ix%2Ft4oish8rLp5kAKAuTbFmTK%2Fimg.png)

> 명령 프롬프트를 실행시킵니다. cmd 창 실행 (윈도우 키 + R, cmd 실행)
>  ```
>  mariadb -V
>  또는 
>  mysql -V
>  ```

### HeidiSLQ를 이용한 DB 접속

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FMWEjS%2FbtrYT9LuJd8%2FNcN02REtVBFsxkPm39hd60%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FGdYyJ%2FbtrY2nBRgzP%2FJ8MAJ2A49KSvSXY62zH5LK%2Fimg.png)

> 에러가 생긴다면, Library를 libmysql.dll 로 변경

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FJcluz%2FbtrYUT2GUDj%2FaMMOsM90Y1iqbStVg0I9k0%2Fimg.png)

> F9를 누르면 선택된 쿼리가 실행

### IntelliJ를 이용한 DB 접속

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbEBNMV%2FbtrMPULFDrQ%2FkN5ZECslS0FqBktL7WEkdK%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FQRLmf%2FbtrMOTGsYyA%2FB8dPaiC2wo4L19aGX079KK%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fctedgb%2FbtrMQB6ecYw%2FcCj3sZTuSbgLLYJZcQwnj0%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fctedgb%2FbtrMQB6ecYw%2FcCj3sZTuSbgLLYJZcQwnj0%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FyTHzm%2FbtrMMaQyqVA%2FcAeHCAvpqiyk5jBHMvp8k0%2Fimg.png)

### DBeaver를 이용한 DB 접속

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdRaqHl%2FbtrKgtwaIcU%2F0lbcUvr4yUFmaC60KRElWK%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FxVYQn%2FbtrJ8mFMuwL%2FFbUcKBsOV7BsF12vyB5AKK%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbDUzaf%2FbtrJ74LkwKJ%2FdxxALQOz4FcXtuf71z9Os0%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdsS8Zp%2FbtrJ71PpFN7%2F1dH9FJSEjZ0MvsgjkLW3RK%2Fimg.png)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdsuabd%2FbtrKetwKXUA%2FocDc8wq7vKuCgcSjYf7QZk%2Fimg.png)

![]()
![]()
![]()

___

### 출처(참고문헌)

- [윈도우에 MariaDB 다운로드](https://congsong.tistory.com/62)
- [MariaDB 환경 변수 설정하기](https://lifere.tistory.com/entry/MariaDB-MariaDB-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0)
- [MariaDB 설치](https://www.youtube.com/watch?v=zOropZAzviQ&list=PLZzruF3-_clsWF2aULPsUPomgolJ-idGJ&index=3)
- [DBeaver 설치, MariaDB 연결](https://backendcode.tistory.com/180)

___

### 연결문서

- [[0.MariaDB란]]
- [[0.IntelliJ]]


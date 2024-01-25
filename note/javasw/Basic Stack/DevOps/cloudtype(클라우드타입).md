### 날짜 : 2024-01-22 14:17

___

### 주제 : #cloudtype #클라우드타입

___

### 생성 : 

![](https://docs.cloudtype.io/_next/static/media/mariadb-1.7a8b8992bc3f2ccdd27c3d8db5d7f461.png)

![](https://docs.cloudtype.io/_next/static/media/mariadb-2.bd92de59f58cdeef1e0cfa06ad334b8c.png)

> 설정변경 을 클릭하고 Root Password 설정 후 배포하기 를 클릭하여 배포를 진행합니다. \
> Root Password 를 별도로 설정하지 않으면 프로젝트 내부에 랜덤값의 암호가 \[서비스명\]-root-password 시크릿으로 설정됩니다. 

### 호스트, 포트

![](https://docs.cloudtype.io/_next/static/media/mariadb-4.aea51d377b6d5468007879047cea575a.png)

> 도메인 탭 : 호스트:포트 조합 확인 합니다.
>> svc ... = TCP 외부 접속에 사용되는 호스트, 포트 입니다.
>> ... : 3306 = 동일 배포환경에서 DB에 접근할 때 사용되는 호스트, 포트 입니다.

### TCP 외부 접속 허용

![](https://docs.cloudtype.io/_next/static/media/mariadb-5.6b927fc7b44412b6960a1989487dc13a.png)

![](https://docs.cloudtype.io/_next/static/media/mariadb-5.6b927fc7b44412b6960a1989487dc13a.png)

>[!note] TCP 외부 접속을 허용해야 하는 경우
>
> - 클라우드타입의 다른 프로젝트에서 배포했거나 동일 프로젝트의 다른 배포환경에서 배포한 서비스에서 접근하는 경우
> - 로컬 환경에서 개발 중인 서비스를 테스트 하기 위해 접근이 필요한 경우
> - 로컬 환경의 DB 툴을 활용해 접근하는 경우

### 연결 :

![](https://docs.cloudtype.io/_next/static/media/mariadb-6.10f225805dc371dadf153a15c0de2bce.png)

> MySQL Workbench를 실행한 후 도메인 탭에서 확인한 호스트명, 포트 번호 및 계정 정보를 아래와 같이 입력하면 클라우드타입에서 배포한 MariaDB와 연결이 완료됩니다.
> 
>> 접속이 되지 않는 경우 TCP 외부 접속 설정을 확인해주세요.

![]()
![]()
![]()
![]()




![]()


>ㅇ

>[!note] 콜아웃

___

### 출처(참고문헌)

- [클라우드타입 이용가이드](https://docs.cloudtype.io/guide/databases/mariadb)

___

### 연결문서

- [[0.DevOps]]


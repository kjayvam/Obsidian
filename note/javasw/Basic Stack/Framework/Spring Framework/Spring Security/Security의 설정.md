### 날짜 : 2024-02-14 09:49

___

### 주제 : #Security #설정
___

### 설명 : 

#### 시작 : 

>[!note] @Override configure(HttpSecurity http)
>
> HTTP 요청에 대한 웹 기반 보안을 설정합니다.

#### 상위 - 인가규칙 : 

>[!note] .authorizeRequests()
>
> URL 경로에 대한 인가 규칙을 설정합니다.

>[!note] .antMatchers("/#", "/#")
>
> (/#, /#) 이후에 호출되는 메서드들이 해당 패턴에 대한 접근 제어를 설정할 수 있게 됩니다.

>[!note] .anyRequest()
>
> 앞서 정의된 규칙 외에 남아있는 모든 요청(anyRequest)에 대한 접근 제어를 설정하기 위해 사용됩니다.

#### 하위 - 인가규칙 : 

>[!note] .authenticated()
>
> 인증(로그인)(authenticated) 후 접근이 가능합니다.

>[!note] .permitAll()
>
> 특정 URL 경로를 인증 없이 허용합니다.
> 인증(로그인) 없이 접근을 허용합니다.

>[!note] .hasRole("")
> 
> 특정 권한을 가진 사용자만 접근을 허용합니다.

>[!note] .hasAnyRole("", "")
> 
> 여러 권한 중 하나라도 가진 사용자에게 접근을 허용합니다.

>[!note] .denyAll()
>
> 모든 사용자, 로그인을 해도 접근 불가능 합니다.

#### 상위 - 회원 : 

>[!note] .formLogin()
> 
> 폼 기반 로그인을 활성화합니다.

>[!note] .logout()
>
> 로그아웃을 처리하는 설정을 추가합니다.

#### 하위 - 회원 : 

>[!note] .loginPage("")
>
> 로그인 페이지의 경로를 지정합니다.

>[!note] .defaultSuccessUrl("")
>
> 로그인 성공 후 이동할 기본 URL을 설정합니다.

>[!note] .failureUrl("")
>
> 로그인 실패 시 이동할 URL을 지정합니다.
> (아이디/비밀번호)가 틀려서 인증에 실패한 경우 설정합니다.

>[!note] .logoutUrl("")
>
> 로그아웃 URL을 지정합니다.

>[!note] .logoutSuccessUrl("")
>
> 로그아웃 성공 후 이동할 URL을 설정합니다.



#### 상위 - 세션 : 

>[!note] .sessionManagement()
>
> 세션 관리를 설정합니다.

>[!note] .sessionCreationPolicy()
>
> 세션 생성 정책을 설정합니다.

#### 하위 - 세션 : 

>[!note] .maximumSessions(정수)
>
> 하나의 아이디에 대한 다중 로그인 허용 갯수

>[!note] .maxSessionsPreventsLogin(boolean);
>
> 다중 로그인 개수를 초과 할 경우 처리 방법
> true : 초과 시 새로운 로그인 차단
> false : 초과 시 기존 세션 하나 삭제

>[!note] .sessionFixation()
>
> 세션에 대한 공격 보호
> .none() : 로그인 시 세션 정보 변경 안 함
> .newSession() : 로그인 시 세션 새로 생성
> .changeSessionId() : 로그인 시 동일한 세션에 대한 id 변경 (추천)





#### 기타 : 

>[!note] .csrf()
>
> CSRF(Cross-Site Request Forgery) 공격 방어 설정을 활성화합니다.
> 

___

### 출처(참고문헌)

- [공식문서](https://spring.io/blog/2022/02/21/spring-security-without-the-websecurityconfigureradapter)
- [스프링시큐리티 설정값들의 역할과 설정방법(2)](https://kimchanjung.github.io/programming/2020/07/02/spring-security-02/)
- [어렵지 않게 설정하기](https://gngsn.tistory.com/155)
- [권한 설정 및 사용 방법](https://cocococo.tistory.com/entry/Spring-Boot-Spring-Security-%EA%B6%8C%ED%95%9C-%EC%84%A4%EC%A0%95-%EB%B0%8F-%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95)

___

### 연결문서

- [[0.Security]]


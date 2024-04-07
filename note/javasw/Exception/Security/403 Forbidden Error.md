### 날짜 : 2024-03-15 05:18

___

### 주제 : #403error

___

### 문제 : 

![](https://velog.velcdn.com/images/minnseong/post/8344c698-9738-4dc0-a253-af3dcaae54e8/image.png)

```java
@AllArgsConstructor 
@Configuration  
@EnableWebSecurity  
public class AppConfig {  

    @Bean  
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {  
  
        // 모든 경로는 인증 없이 허용, 이외 모든 요청은 로그인이 필요합니다.  
        http.authorizeRequests().antMatchers("/**").permitAll().anyRequest().authenticated();  
        // 로그인폼의 위치는 "/login"이고 로그인 성공시 "/"로 이동합니다.  
        http.formLogin().loginPage("/login").defaultSuccessUrl("/");  
        // 로그아웃 시 "/"로 이동합니다.  
        http.logout().logoutUrl("/logout").logoutSuccessUrl("/");  
        // 다중 중복 로그인  
        http.sessionManagement().maximumSessions(5).maxSessionsPreventsLogin(false);  
        // 로그인 성공시 세션 보호  
        http.sessionManagement().sessionFixation().changeSessionId();  
        //http.csrf().disable();  
  
        return http.build();  
    }
}
```

### 원인 : 

>[!note] 403 Forbidden 에러가 발생하는 가장 흔한 원인은 다음과 같습니다.
> 
> 1. 인증되지 않은 접근
> 	- 보호된 리소스에 인증 토큰이 없이 접근할 경우
> 2. 권한이 없는 접근
>	- 인증은 되었지만 리소스에 대한 접근 권한이 없을 경우
> 3. CSRF(Cross-Site Request Forgery) 보호 기능
>	- 서버에 저장된 CSRF 토큰과 요청의 토큰이 일치하지 않아 발생
> 4. CORS(Cross-Origin Resource Sharing) 오류
> 	- 요청한 출처가 리소스 접근을 허용하지 않는 Origin인 경우
> 
> 대부분의 경우 1, 2번 인증이나 권한 문제이며, Spring Security 설정을 확인해야 합니다.
> 3, 4번의 경우는 CSRF나 CORS 설정문제로 추가 설정이 필요합니다.
> 구체적으로 어떤 요청에서 403이 발생하는지 로그를 통해 확인이 필요합니다.

> 저의 경우 2번(권한이 없는 접근)으로 403 에러가 발생했던 원인은 CSRF 보호 설정에서 기인했던 것 같습니다.
> Spring Security에서는 기본적으로 CSRF 보호 기능이 활성화되어 있습니다.
> 이 설정에 의해 별도의 CSRF token 전달 없이 stateless한 RESTful API 요청이 들어오면 403 Forbidden 에러가 발생하게 됩니다.

### 해결 방안 1 : 

>[!note] CSRF 비활성화
>
> ```java
> http.csrf().disable();
> ```
> 을 추가해서 에러를 해결
> 
>> 하지만 Security는 CSRF 공격에 대한 방지를 수행한다.
>> 1. CSRF 공격으로 인한 보안 문제가 발생할 수 있습니다.
>> 2. 사용자의 개인 / 중요 정보가 유출될 수 있습니다.
>> 3. 시스템의 무결성이 훼손됩니다.
>
> 그렇기 때문에 CSRF 방어 기능을 유지하면서 특정 요청에 대한 예외를 허용하는 것이 더 안전한 방법입니다.
> 
> - CORS 요청 시 예외 허용
> - AJAX 요청 시 예외 허용 등
> 
> 가능하다면 CSRF 방어 기능을 활성화한 채로 애플리케이션을 운영하는 것이 바람직합니다.

### 해결 방안 2 :

>[!note] CSRF 방어 기능은 활성화된 채로,  CSRF 토큰을 검증하지 않도록 예외 처리
>
> ```java
> http.csrf().ignoringAntMatchers("/**");
> ```
> 
> 보안 유지가 필요하므로 인증/인가를 풀어주는 경우 보다는 CSRF만 허용하는 편이 안전합니다.

> 여기서 ignoringAntMatchers()를 사용하여 특정 경로를 예외로 지정한 후에 403 에러가 사라진 것을 보면, 처음에 걸렸던 에러가 바로 CSRF 보호 설정에 의한 것이었다고 추측해볼 수 있습니다.
> 즉, CSRF 보호 대상에서 제외시킴으로써 정상 동작하도록 했다고 볼 수 있습니다.

___

### 출처(참고문헌)

- [403 에러](https://velog.io/@minnseong/Spring-Security-403-Forbidden-%EC%97%90%EB%9F%AC)

___

### 연결문서

- [[0.Security]]


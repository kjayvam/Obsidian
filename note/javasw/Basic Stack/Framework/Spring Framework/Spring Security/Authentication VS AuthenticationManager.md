### 날짜 : 2024-03-21 03:27

___

### 주제 : #Authentication #인증 #AuthenticationManager #인증관리자 #비교 

___

### 요약 : 

>[!note] Authentication (인증)
>
> `Authentication` 방식은 사용자 인증 절차 없이 사용자 정보를 `SecurityContext`에 설정하는 방식

>[!note] AuthenticationManager (인증관리자)
>
> `AuthenticationManager`를 통해 사용자 인증 절차를 실제로 수행한 후 인증된 사용자 정보를 `SecurityContext`에 설정하는 방식입니다. 
> 보안을 위해, 사용자 인증 정보를 검증하는 두 번째 방식을 사용하는 것이 중요합니다.

### 이유 : 

> 세션에 저장하는 방법도 하나의 방법이지만,
> 스프링 시큐리티를 사용하는 경우, 일반적으로는 Security Context를 통해 사용자 인증을 관리합니다. 
> 세션에 직접 사용자 정보를 저장하는 것은 필요한 경우에만 사용해야 합니다.
> 
> 1. 표준화된 접근 방식 : 스프링 시큐리티의 `SecurityContext`를 사용하면, 인증된 사용자의 정보를 얻기 위한 표준화된 방법을 사용할 수 있습니다. 이는 애플리케이션의 다양한 부분에서 일관된 방식으로 인증 정보에 접근할 수 있게 해주며, 보안 관련 코드의 유지 보수성을 향상시킵니다.
> 2. 자동 관리 : 스프링 시큐리티는 `SecurityContext`의 생명주기를 자동으로 관리합니다. 예를 들어, 요청이 시작될 때 인증 정보를 로드하고, 요청이 종료될 때 이를 정리하는 과정을 자동으로 수행합니다. 이는 개발자가 이러한 세부 사항에 대해 걱정하지 않아도 되게 해줍니다.
> 3. 확장성과 유연성 : 스프링 시큐리티는 다양한 인증 메커니즘을 지원합니다. 예를 들어, 폼 기반 인증, HTTP 기본 인증, OAuth 등 다양한 방식을 쉽게 구현할 수 있습니다. `SecurityContext`를 사용하면, 이러한 다양한 인증 방식을 통합적으로 관리할 수 있습니다.
> 4. 보안 기능 : 스프링 시큐리티는 CSRF 방어, 세션 고정 보호, 비밀번호 저장 방식 등의 보안 기능을 제공합니다. 이러한 기능들은 `SecurityContext`와 밀접하게 통합되어 있으며, 세션을 직접 관리할 때 이러한 보안 기능들을 효과적으로 활용하기 어려울 수 있습니다.
> 5. 세션 독립성 : 일부 애플리케이션은 세션을 사용하지 않는 상태로 동작할 수 있어야 합니다. 예를 들어, REST API는 상태를 유지하지 않는(stateless) 통신을 선호합니다. `SecurityContext`를 사용하면, 세션 기반 인증과 세션을 사용하지 않는 인증을 모두 지원할 수 있습니다.
> 
> 이러한 이유들로 인해, 스프링 시큐리티를 사용하는 경우 일반적으로 `SecurityContext`를 통해 사용자 인증 정보를 관리하는 것이 좋습니다. 
> 필요한 경우가 아니라면 세션에 직접 사용자 정보를 저장하는 것은 피하는 것이 좋습니다.

### 설명 : 

>[!note] Authentication (인증)
>
> ```java
> Authentication authentication = 
> 				new UsernamePasswordAuthenticationToken(username, password);
> SecurityContextHolder.getContext().setAuthentication(authentication);
> ```
> 
> `UsernamePasswordAuthenticationToken` 객체를 생성하고, 이를 `SecurityContextHolder`에 직접 설정합니다. 
> 하지만, 여기서 중요한 점은 이 방식으로는 실제로 사용자의 인증 절차(즉, 사용자 이름과 비밀번호가 올바른지 확인하는 절차)를 수행하지 않습니다. 
> `UsernamePasswordAuthenticationToken`을 생성하고 `SecurityContextHolder`에 설정하기만 할 뿐, 사용자의 인증 정보가 올바른지, 사용자가 존재하는지 등을 검증하지 않습니다. 
> 이는 보안상 매우 위험할 수 있으며, 일반적으로 권장되지 않습니다.

>[!note] AuthenticationManager (인증관리자)
>
> ```java
> private AuthenticationManager authenticationManager;
> 
> UsernamePasswordAuthenticationToken authReq = 
> 				new UsernamePasswordAuthenticationToken(username, password);
> Authentication auth = authenticationManager.authenticate(authReq);
> SecurityContextHolder.getContext().setAuthentication(auth);
> ```
> 
> `AuthenticationManager`를 사용하여 사용자의 인증 정보를 실제로 검증합니다. 
> `UsernamePasswordAuthenticationToken` 객체를 `AuthenticationManager`의 `authenticate()` 메소드에 전달함으로써, 사용자 이름과 비밀번호가 유효한지 확인합니다. 
> 이 과정에서 `AuthenticationManager`는 내부적으로 `UserDetailsService`를 호출하여 제공된 사용자 이름에 해당하는 사용자 정보를 불러오고, 비밀번호가 일치하는지 확인합니다. 
> 인증이 성공적으로 이루어지면, 인증된 사용자 정보를 나타내는 `Authentication` 객체가 반환됩니다. 
> 그런 다음, 이 객체를 `SecurityContextHolder`에 설정하여 애플리케이션 전역에서 현재 인증된 사용자의 정보에 접근할 수 있도록 합니다.

### AuthenticationManager 사용 방법 : 

```java
@Autowired  
private AuthenticationManager authenticationManager;

    public String login(username, password) {  
	    // 인증 토큰 생성
        UsernamePasswordAuthenticationToken authReq = 
			        new UsernamePasswordAuthenticationToken(username, password);
		// 정상인지 로그인 시도 해봄. authenticationManager로 로그인 시도를 하면  
		// PrincipalDetailsService가 호출 loadUserByUsername() 함수가 실행된 후 정상이면 authentication이 리턴됨.  
		// authentication이 정상 리턴된다는 것은 -> DB에 있는 username과 password가 일치한다는 것.
		Authentication auth = authenticationManager.authenticate(authReq);
		// 홈페이지 어디서든 인증 정보 확인 가능
		SecurityContextHolder.getContext().setAuthentication(auth);  
  
		return "";  
    }
```

>[!note] Spring Security 5 이전 버전
>
> ```java
> @EnableWebSecurity
> public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
> 
>     @Bean
>     @Override
>     public AuthenticationManager authenticationManagerBean() throws Exception {
>         return super.authenticationManagerBean();
>     }
> }
> ```

>[!note] Spring Security 5 이후 버전
>
> ```java
> @EnableWebSecurity
> public class SecurityConfig {
> 
> 	@Bean  
> 	public AuthenticationManager authenticationManager(AuthenticationConfiguration authenticationConfiguration) throws Exception {  
> 		return authenticationConfiguration.getAuthenticationManager();  
> 	}
> 	
> 	@Bean  
> 	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
> 	}
> }
> ```

>[!note] AuthenticationManager 빈의 구성이 SecurityFilterChain 빈 구성보다 먼저 이루어지도록 코드를 조정해야하는 이유
>
> 1. 인증 프로세스의 핵심 요소 : `AuthenticationManager`는 인증 과정의 핵심적인 요소로, 사용자의 인증 정보(예: 사용자 이름과 비밀번호)를 받아 인증을 수행합니다. 인증이 성공하면, 인증된 사용자에 대한 `Authentication` 객체를 반환합니다. 이러한 인증 과정은 대부분의 시큐리티 필터 체인 내부에서 수행되기 때문에, 필터들이 올바르게 작동하기 위해서는 `AuthenticationManager`가 먼저 구성되어 있어야 합니다.
> 2. 초기화 및 의존성 순서 : 스프링 시큐리티의 설정 과정에서 `SecurityFilterChain`을 구성하는 것은 여러 시큐리티 필터들을 초기화하고 적절한 순서로 연결하는 작업을 포함합니다. 이 필터들 중 일부는 인증을 처리하기 위해 `AuthenticationManager`에 의존합니다. 따라서, `SecurityFilterChain`이 적절하게 작동하기 위해서는 `AuthenticationManager`가 먼저 초기화되고 사용 가능한 상태여야 합니다.
> 3. 구성의 명확성과 오류 방지 : `AuthenticationManager`를 먼저 구성함으로써, 스프링의 의존성 주입 과정에서 명확한 의존성 관계를 설정할 수 있습니다. 이는 구성 오류를 방지하고, 스프링 애플리케이션의 초기화 과정에서 발생할 수 있는 문제를 최소화하는 데 도움이 됩니다.
> 4. 예를 들어, Java 설정을 사용하는 스프링 시큐리티 프로젝트에서는 `WebSecurityConfigurerAdapter`를 확장하여 `configure(AuthenticationManagerBuilder auth)` 메서드를 오버라이드하고, `AuthenticationManager`를 구성할 수 있습니다. 이후, `configure(HttpSecurity http)` 메서드 내에서 `http`를 사용하여 `SecurityFilterChain`을 구성하는데, 이 때 이미 `AuthenticationManager`가 구성되어 있어야 합니다.
>  
>> 결론적으로, `AuthenticationManager` 빈의 구성이 `SecurityFilterChain` 빈 구성보다 먼저 이루어져야 하는 것은 스프링 시큐리티의 인증 처리 과정에 있어 `AuthenticationManager`의 중요성과 필터 체인 내에서의 의존성 때문입니다. 이를 통해 스프링 시큐리티는 효율적이고 안정적인 인증 처리를 제공할 수 있습니다.

___

### 출처(참고문헌)

- [스프링 시큐리티 - Authentication, SecurityContext](https://velog.io/@gmtmoney2357/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%8B%9C%ED%81%90%EB%A6%AC%ED%8B%B0-Authentication-SecurityContext)
- [Authentication/HttpSesession 값 반영](https://velog.io/@armton/%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EC%A4%91%EC%9D%B8-%EC%9C%A0%EC%A0%80-%EC%A0%95%EB%B3%B4-%EC%88%98%EC%A0%95-%EC%8B%9C-Spring-security-AuthenticationHttpSesession-%EA%B0%92-%EB%B0%98%EC%98%81)
- [Authentication 바꿔주기](https://tmdrl5779.tistory.com/78)
- [WebSecurityConfigurerAdapter 없이 구성() 구현하기](https://velog.io/@waveofmymind/Spring-Security-WebSecurityConfigurerAdapter-%EC%97%86%EC%9D%B4-configure-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0)

___

### 연결문서

- [[0.Security]]


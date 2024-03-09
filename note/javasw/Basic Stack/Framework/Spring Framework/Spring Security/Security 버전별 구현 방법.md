### 날짜 : 2024-02-16 10:55

___

### 주제 : #Security #버전별 #구현방법

___

### 버전별 특징 : 

스프링은 버전에 따라 구현 방식이 변경되는데 시큐리티의 경우 특히 세부 버전별로 구현 방법이 많이 다르기 때문에 버전 마다 구현 특징을 확인해야 한다.

새로운 버전이 출시될 때마다 [GitHub의 Spring 리포지토리에서 Security의 Release 항목](https://github.com/spring-projects/spring-security/releases)을 통해 변경된 점을 확인할 수 있다.

### 주요 버전별 구현 :

- 스프링 부트 2.X.X ~ 2.6.X (스프링 5.X.X ~ 2.6.X

```java
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {

	@Override
	protected void configure(HttpSecurity http) throws Exception {
		http
			.authorizeRequests()
			.antMatchers("/").authenticated()
			.anyRequest().permitAll();
	}
}
```

- 스프링 부트 2.7.X ~ 3.0.X (스프링 5.7.X M2 ~ 3.0.X)

```java
public class SpringSecurityConfig {

	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http
			.authorizeHttpRequests()
			.requestMatchers("/admin").hasRole("ADMIN")
			.anyRequest().authenticated();

		return http.build();
	}
}
```

- 스프링 부트 3.1.X ~ (스프링 6.1.X ~ )

```java
public class SpringSecurityConfig {

	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http
			.authorizeHttpRequests((auth) -> auth
			.requestMatchers("/login", "/join").permitAll()
			.anyRequest().authenticated()
			);

		return http.build();
	}
}
```

> 3.1.X 버전 부터 람다형식 표현 필수

___

### 출처(참고문헌)

- [시큐리티 버전별 구현 방법](https://substantial-park-a17.notion.site/f3cbc92735824274a570dd81284cac56)

___

### 연결문서

- [[0.Security]]


### 날짜 : 2024-02-13 16:00

___

### 주제 : #Security  #BCryptPasswordEncoder

___

### 설명 : 

>[!note] BCryptPasswordEncoder
>
> 비밀번호 암호화를 위한 클래스
> 
> - 비밀번호를 암호화할 때 BCrypt 해싱 함수를 사용합니다.
> 	- BCrypt는 강력한 1방향 암호화 알고리즘으로 보안성이 뛰어납니다.
> - 동일한 비밀번호에 대해서도 매번 다른 암호화된 결과를 생성합니다.
> 	- 이는 레인보우 테이블 공격을 어렵게 만듭니다.
> - BCrypt 해시를 사용하면 횟수(strength)를 조정할 수 있습니다.
> 	- 횟수를 높일 수록 암호화에 시간과 리소스가 더 소모되지만 보안성은 높아집니다.
> - encode() 메서드를 사용해 비밀번호를 암호화합니다.
> - matches() 메서드를 사용해 평문과 암호화된 해시를 비교, 검증합니다.

### 사용법 : 

```java
@Configuration
public class AppConfig {

    @Bean
    public BCryptPasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }

}
```

> 스프링 부트에서 기본적으로 `BCryptPasswordEncoder` 빈을 생성하지 않습니다. 
> 직접 빈으로 등록해주어야 합니다.

```java
@Service
public class MemberService {

    @Autowired
    private BCryptPasswordEncoder passwordEncoder;

    public Member signup(Member member) {
        String encodedPw = passwordEncoder.encode(member.getPw());
        member.setPw(encodedPw);
        return memberRepository.save(member);
    }

    public Member login(String id, String pw) {
        Member member = memberRepository.findById(id);
        if(passwordEncoder.matches(pw, member.getPw())) {
            return member;
        } 
        return null;
    }

}
```

```java
// Repository 
@Repository
public interface MemberRepository extends JpaRepository<Member, Long> {
    
    @Query("select m from Member m where m.id = :id")
    Member findById(@Param("id") String id);

}
```

___

### 출처(참고문헌)

- [공식문서](https://docs.spring.io/spring-security/reference/features/authentication/password-storage.html#authentication-password-storage-bcrypt)
- [BCryptPasswordEncoder란?](https://bestinu.tistory.com/60)

___

### 연결문서

- [[0.Security]]

